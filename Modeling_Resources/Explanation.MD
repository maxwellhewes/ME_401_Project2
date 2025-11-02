# Modeling Reference: Governing Physics + Applied Math Foundations

**A Field Guide for Connecting Real Physics to Computational Models**

---

## Introduction: Why This Matters

You've learned thermodynamics, heat transfer, and fluid mechanics in lecture. Now it's time to **make those concepts move**—to watch energy flow through a system in real time, to predict how a reactor behaves under different conditions, to explore designs that don't yet exist.

This document is your entry point. It won't teach you every detail, but it will show you **what questions to ask** and **where to start**. Think of it as a map: each concept below is a trailhead. Your job is to pick one, take a few steps, and see where curiosity leads you.

---

## How to Use AI as Your Research Partner

You're not expected to know everything. You *are* expected to learn how to learn. AI tools (like the one you're using right now) can be **extraordinary research accelerators**—if you ask good questions.

### **What to Ask AI:**
- **"Explain the physical meaning of [term] in this equation."**  
  *(e.g., "What does the convective heat transfer coefficient represent in real systems?")*
- **"What numerical method should I use to solve [type of equation]?"**  
  *(e.g., "How do I solve a system of coupled ODEs?")*
- **"Show me the units of each term and check if this equation is dimensionally consistent."**
- **"What assumptions are hidden in this model?"**
- **"How would I extend this model to include [physical effect]?"**

### **What NOT to Ask:**
- **"Give me the answer to this problem."** *(You learn nothing.)*
- **"Write all the code for me."** *(You won't understand what breaks.)*

### **Golden Rule:**
**Ask AI to teach you, not to do the work for you.** Use it to clarify concepts, check your reasoning, and explore new techniques. You're building intuition, not collecting solutions.

---

## Core Concepts

---

### 1. Energy Balance (First Law of Thermodynamics)

**What It Describes:**  
Energy cannot be created or destroyed—only transferred or converted. Every thermal or energy system obeys this principle. An energy balance tells you how energy flows into, out of, and accumulates within a control volume (like a reactor, heat exchanger, or power cycle component).

**Mathematical Form:**
$$\frac{dU}{dt} = \dot{Q} - \dot{W} + \sum \dot{m}_i h_i - \sum \dot{m}_e h_e$$

Where:
- $U$ = internal energy of the system
- $\dot{Q}$ = heat transfer rate into the system
- $\dot{W}$ = work done by the system
- $\dot{m}h$ = enthalpy flow (mass flow rate × specific enthalpy)

**Why It Matters:**  
This is the foundation of reactor design, cogeneration analysis, and thermodynamic cycle modeling. If you can't write an energy balance, you can't predict system behavior.

**Progression Path:**
1. **Simple:** Isothermal tank being heated—solve for temperature rise over time (lumped capacitance, no spatial variation).
2. **Realistic:** Add heat loss to surroundings (convection term), inlet/outlet flows with different temperatures.
3. **Research-Grade:** Couple energy balance to reaction kinetics (exothermic reactions generate heat, affecting conversion rates).

**First Numerical Steps:**
- Set up a **time-dependent ordinary differential equation (ODE)** for a closed system gaining heat.
- Use an **ODE solver** (Euler method, Runge-Kutta, or built-in solvers) to compute temperature vs. time.
- **Ask AI:** "How do I numerically integrate an ODE that describes heat transfer into a tank?"

**Questions to Explore:**
- What happens if heat input varies with time (e.g., sinusoidal, step change)?
- How do I handle multiple streams entering/exiting at different temperatures?
- What changes if the system is at steady-state instead of transient?

---

### 2. Mass Balance (Continuity Equation)

**What It Describes:**  
Mass is conserved. In reactive systems (like hydrothermal carbonization), species are created and consumed. A mass balance tracks how much of each component is present over time or space.

**Mathematical Form:**
$$\frac{dm_i}{dt} = \sum \dot{m}_{i,in} - \sum \dot{m}_{i,out} + \dot{r}_i V$$

Where:
- $m_i$ = mass of species $i$ in the control volume
- $\dot{m}_{i,in/out}$ = mass flow rates of species $i$
- $\dot{r}_i$ = reaction rate (mass per volume per time)
- $V$ = reactor volume

**Why It Matters:**  
Predicting conversion, yield, and product composition in any chemical or biochemical process requires tracking species mass balances.

**Progression Path:**
1. **Simple:** Single reactant in a batch reactor—solve for concentration decay (first-order kinetics, no flow).
2. **Realistic:** Continuous stirred-tank reactor (CSTR) with inlet/outlet streams and reaction.
3. **Research-Grade:** Multiple species, coupled reactions (e.g., biomass → intermediates → char/gas products).

**First Numerical Steps:**
- Write a **differential equation for concentration** of a single species undergoing reaction.
- Solve using an ODE solver; plot concentration vs. time or residence time.
- **Ask AI:** "What's the difference between a batch reactor and a CSTR in terms of mass balance equations?"

**Questions to Explore:**
- How does residence time affect conversion in a continuous reactor?
- What if multiple reactions occur in parallel or series?
- How do I incorporate stoichiometry into the mass balance for multiple species?

---

### 3. Reaction Kinetics (Arrhenius Law)

**What It Describes:**  
Chemical reactions speed up with temperature. Kinetics quantifies *how fast* reactions proceed and how temperature, concentration, and catalysts influence that rate.

**Mathematical Form:**
$$r = k(T) \cdot f(C_i)$$
$$k(T) = A e^{-E_a / RT}$$

Where:
- $r$ = reaction rate
- $k(T)$ = temperature-dependent rate constant (Arrhenius form)
- $A$ = pre-exponential factor (frequency of collisions)
- $E_a$ = activation energy (barrier to reaction)
- $R$ = universal gas constant
- $T$ = absolute temperature
- $f(C_i)$ = concentration dependence (e.g., $C^n$ for $n$-th order reaction)

**Why It Matters:**  
Kinetics bridges thermodynamics (what *can* happen) and real-world operation (what *does* happen). Without kinetics, you can't predict reactor size, residence time, or operating temperature.

**Progression Path:**
1. **Simple:** Fit experimental data to find $A$ and $E_a$ (linear regression on $\ln(k)$ vs. $1/T$).
2. **Realistic:** Integrate kinetics into a mass balance to predict conversion vs. time.
3. **Research-Grade:** Multi-step mechanisms with intermediate species; sensitivity analysis on kinetic parameters.

**First Numerical Steps:**
- Take experimental rate data at different temperatures; linearize Arrhenius equation and extract activation energy.
- Couple kinetic expression to a mass balance ODE.
- **Ask AI:** "How do I perform nonlinear regression to fit kinetic parameters to experimental data?"

**Questions to Explore:**
- How sensitive is reactor performance to a 10°C temperature change?
- What if the reaction is reversible (equilibrium-limited)?
- How do I identify the rate-limiting step in a multi-step mechanism?

---

### 4. Heat Transfer (Conduction, Convection, Radiation)

**What It Describes:**  
Heat moves through materials (conduction), across boundaries (convection), and via electromagnetic waves (radiation). Modeling heat transfer predicts temperature distributions in space and time.

**Mathematical Form (Conduction):**
$$\frac{\partial T}{\partial t} = \alpha \nabla^2 T$$

Where:
- $\alpha = k / (\rho c_p)$ is thermal diffusivity
- $k$ = thermal conductivity
- $\rho$ = density
- $c_p$ = specific heat

**Convective Boundary Condition:**
$$-k \frac{\partial T}{\partial n}\bigg|_{surface} = h(T_{surface} - T_{\infty})$$

Where $h$ is the convective heat transfer coefficient.

**Why It Matters:**  
Temperature governs reaction rates, material properties, and safety limits. Heat transfer modeling is essential for reactor design, heat exchangers, and thermal management.

**Progression Path:**
1. **Simple:** 1D transient conduction in a slab with fixed boundary temperatures (analytical solution exists; compare to numerical).
2. **Realistic:** Add convective cooling at boundaries; solve using finite difference method.
3. **Research-Grade:** Couple temperature field to reaction kinetics (exothermic reactions create internal heat generation).

**First Numerical Steps:**
- Discretize space into a grid; approximate spatial derivatives using finite differences.
- March forward in time using explicit or implicit time-stepping.
- **Ask AI:** "Explain the difference between explicit and implicit methods for solving the heat equation."

**Questions to Explore:**
- What grid size and time step are needed for numerical stability?
- How does insulation (low $k$) or high convection (large $h$) affect the solution?
- What happens if thermal properties ($k$, $\rho$, $c_p$) vary with temperature?

---

### 5. Entropy Generation (Second Law of Thermodynamics)

**What It Describes:**  
Real processes are irreversible—energy quality degrades. Entropy generation quantifies lost work potential due to friction, heat transfer across finite temperature differences, mixing, and chemical reactions.

**Mathematical Form:**
$$\dot{S}_{gen} = \dot{S}_{out} - \dot{S}_{in} - \frac{\dot{Q}}{T_b} \geq 0$$

For a control volume:
$$\dot{S}_{gen} = \sum \dot{m}_e s_e - \sum \dot{m}_i s_i - \sum \frac{\dot{Q}_j}{T_j}$$

Where:
- $s$ = specific entropy
- $\dot{Q}_j / T_j$ = entropy transfer due to heat at boundary temperature $T_j$

**Why It Matters:**  
Entropy generation reveals inefficiencies. Minimizing it improves cycle efficiency, cogeneration performance, and process economics. It's the foundation of exergy analysis.

**Progression Path:**
1. **Simple:** Calculate entropy generation for a heat exchanger with known inlet/outlet states.
2. **Realistic:** Compute entropy generation rate in a reactor with chemical reaction and heat transfer.
3. **Research-Grade:** Perform exergy analysis to identify dominant irreversibilities; optimize operating conditions to minimize entropy production.

**First Numerical Steps:**
- Use property tables or equations of state to compute entropy at different states.
- Sum entropy flows and compare to theoretical reversible limit.
- **Ask AI:** "What's the relationship between entropy generation and exergy destruction?"

**Questions to Explore:**
- Which contributes more to entropy generation: heat transfer or chemical reaction?
- How does operating closer to equilibrium reduce irreversibility?
- What is the Gouy-Stodola theorem and how does it link entropy to lost work?

---

### 6. Coupled Systems (Multi-Physics Modeling)

**What It Describes:**  
Real systems don't obey one equation in isolation. Energy balances affect temperature, which affects reaction rates, which generate heat, which alters temperature further. Coupled systems capture these feedbacks.

**Mathematical Form (Example: Exothermic Reactor):**
$$\frac{dC}{dt} = -k(T) C^n \quad \text{(mass balance)}$$
$$\frac{dT}{dt} = \frac{\Delta H_r}{\rho c_p V} \cdot r(C,T) \cdot V - \frac{UA}{\rho c_p V}(T - T_{\infty}) \quad \text{(energy balance)}$$

Where:
- $C$ = reactant concentration
- $T$ = reactor temperature
- $\Delta H_r$ = heat of reaction (negative for exothermic)
- $UA$ = overall heat transfer coefficient × area

**Why It Matters:**  
Coupling reveals emergent behavior: thermal runaway, oscillations, optimal operating windows. This is where modeling becomes predictive and powerful.

**Progression Path:**
1. **Simple:** Solve mass balance assuming constant temperature; then solve energy balance assuming constant concentration. Compare.
2. **Realistic:** Couple the two ODEs; solve simultaneously using a system ODE solver.
3. **Research-Grade:** Add pressure-dependent properties, multi-phase behavior, or control strategies (feedback loops).

**First Numerical Steps:**
- Write a system of ODEs (vector form: $d\mathbf{y}/dt = \mathbf{f}(\mathbf{y}, t)$ where $\mathbf{y} = [C, T]$).
- Solve using a stiff ODE solver if time scales differ greatly.
- **Ask AI:** "What makes an ODE system 'stiff' and why do I need a special solver?"

**Questions to Explore:**
- What happens if cooling is insufficient (runaway scenario)?
- How do I find steady-state solutions (set $d/dt = 0$)?
- Can I linearize near a steady state to analyze stability?

---

## Final Thoughts: From Equations to Insight

Modeling isn't about memorizing formulas—it's about **building physical intuition through computation**. Every equation in this guide represents a conversation between mathematics and reality.

Your goal over the next two weeks isn't to master every technique. It's to:
- **Pick one concept** and make it work.
- **Ask good questions** when you get stuck.
- **Iterate**—start simple, add complexity, learn from failures.

The best models are the ones you understand deeply, not the ones that look impressive. Start small. Build confidence. Then scale up.

**You've got this. Now go build something.**

---

## Recommended Next Steps
1. Choose one concept above that connects to your project interest.
2. Write the simplest possible version of the governing equation.
3. Solve it numerically (even crudely—Euler's method works!).
4. Plot the result. Does it make physical sense?
5. Ask AI to help you interpret, extend, or debug.
6. Repeat with added complexity.

---

*This guide was designed to empower, not overwhelm. If you're curious about something not covered here, that's a sign you're thinking like a researcher. Chase it.*
