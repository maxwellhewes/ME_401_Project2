# Project 2: Applied Thermal/Fluids Mini Projects

In **Project 2**, each student (or group of up to two) will complete one elective mini-project. These projects apply **Thermal/Fluids sciences** to real-world problems through estimation, modeling, decision-making with limited data, and critical evaluation — skills used daily in industry.

Projects are **self-contained and flexible**, allowing creativity and open-ended exploration. You may work **individually or in pairs**.

---

## Deliverables (for all projects)

- **Technical Report (3–4 pages)**
  - Include: Introduction, Methods, Results, Discussion, and Conclusions.
  - Must be professional, clearly written, and created using **Overleaf**.
  - Submit as a **PDF**.

- **Figures, Plots, and Diagrams**
  - At least 2–3 figures or plots (generated via Python, Excel, MATLAB, or COMSOL).

- **Comparative Analysis or Optimization Results**
  - Use your data to compare multiple options or optimize a design/process.

- **Recommendation or Summary Conclusion**
  - Provide a reasoned engineering recommendation based on your analysis.

> You may use Python / Matlab scripts, sample data, or COMSOL models. Focus on **sound engineering judgment**, **meaningful analysis**, and **clear communication**.

---

## Grading Rubric (15 points total)

| Criterion | Points | Description |
|------------|--------|-------------|
| **AI Use Documentation** | 1 | Transparent documentation of AI use. |
| **Introduction & Context** | 2 | Clear project objective, application, and background. |
| **Methodology & Tools** | 2 | Transparent workflow, assumptions, and tool use. |
| **Results & Analysis** | 2 | Clear figures, plots, comparative or optimization results. |
| **Discussion & Trade-offs** | 2 | Critical evaluation of alternatives and system trade-offs. |
| **Recommendation & Conclusion** | 3 | Justified engineering recommendation. |
| **Report Quality & Professionalism** | 3 | Organization, clarity, formatting, and citations. |

---

## Project Options

### **Project A: Hydrothermal Carbonization (HTC) of Biomass**

**Objective:**  
Investigate the behavior of different biomass feedstocks (e.g., algae, wood, food waste) in a hydrothermal carbonization (HTC) process. Determine which feedstocks yield the most usable energy or sequester the most carbon.

**Background:**  
HTC converts wet biomass into a coal-like solid (hydrochar) under high temperature and pressure in water — a promising method for sustainable waste management and energy recovery.

**Suggested Steps:**
1. Research HTC: chemical principles, energy flows, and real-world applications.
2. Select ≥3 feedstocks to compare.
3. Estimate or simulate:
   - Energy content (heating value)
   - Carbon yield or emissions reduction
   - Conversion efficiency
4. Identify key variables (temperature, residence time, moisture content).
5. Recommend the most effective feedstock and operating range for:
   - **Maximum energy output**, or  
   - **Maximum carbon sequestration**

**Tool Ideas:**  
Python / Excel / MATLAB simulation for HTC yield and energy content  
COMSOL reference models (pyrolysis, batch reactor)

**Common Questions:**
- Which feedstock performs best and why?  
- How does moisture content affect HTC efficiency?  
- What trade-offs exist between feedstock availability and energy recovery?

---

### **Project B: Wastewater Treatment & Cogeneration**

**Objective:**  
Design or evaluate a system that uses **anaerobic digestion** and **cogeneration (CHP)** to recover energy from wastewater sludge. Compare performance to conventional treatment plants using only grid electricity.

**Background:**  
Wastewater treatment plants are energy-intensive. Anaerobic digestion can convert sludge into **biogas**, fueling CHP systems to generate both **electricity and heat**, improving sustainability and reducing costs.

**Suggested Steps:**
1. Diagram a wastewater system with anaerobic digesters and CHP.
2. Estimate biogas production per unit wastewater.
3. Perform energy balance calculations to estimate:
   - Electrical energy generation  
   - Heat recovery  
   - Total system efficiency
4. Compare system emissions and energy use to a grid-only plant.
5. Recommend upgrades or designs for improved performance.

**Tool Ideas:**  
Python / MATLAB calculators for energy and emissions  
COMSOL engine/reactor models for heat/flow analysis

**Common Questions:**
- Is the biogas energy sufficient to power the plant?  
- How much grid electricity can be offset?  
- What is the payback time for a CHP upgrade?

---

### **Project C: Thermodynamic Cycle Comparison**

**Objective:**  
Compare and evaluate the performance of four thermodynamic cycles — **Otto**, **Diesel**, **Brayton**, and **Rankine** — for a chosen real-world application. Recommend the most suitable cycle based on performance metrics and constraints.

**Background:**  
Each cycle suits different applications (e.g., Otto for cars, Brayton for turbines). Understanding their trade-offs is key to system design.

**Suggested Steps:**
1. Choose an application (e.g., car engine, jet turbine, power plant, drone).
2. For each cycle:
   - Sketch or simulate **T–s** and **P–v** diagrams.  
   - Calculate ideal or real-world efficiency.  
   - Estimate power output, heat input, and operating range.
3. Consider:
   - Working fluid  
   - Operating temperatures and pressures  
   - Practical constraints (size, cost, emissions)
4. Recommend the optimal cycle for your chosen application.

**Tool Ideas:**  
Python / Excel / MATLAB simulators for ideal cycles and plotting  
COMSOL thermal/mechanical models

**Common Questions:**
- Which cycle provides the best efficiency for your application?  
- How do simplicity, cost, or scale affect your choice?  
- What factors matter most — fuel type, temperature limits, or energy density?

---

## Key Takeaway

These projects are designed to **bridge theory and application**, encouraging exploration, creativity, and rigor. Focus on **clarity of thought, transparency of assumptions, and defensibility of results** — hallmarks of strong engineering practice.
