# fitness-tracker-design
Fitness Tracker Pseudocode and Flowchart and IPO Chart

# Software Design: Campus Fitness & Activity Tracker

**Course:** Software Design & Logic  
**Author:** [Student Name]  
**Deliverable:** Algorithm Design (IPO, Flowchart, Pseudocode)  

---

## 1. Problem Description & Scope
* **Problem:** Students need a command-line interface to track daily cardiovascular and strength exercise durations, validate that inputs are realistic, and review their progress toward a weekly target of 120 minutes.
* **Scope:** 
  * Features a continuous main loop with two hierarchical submenus (Cardio and Strength).
  * Validates menu bounds (rejects values outside menu options) and duration inputs (rejects negative numbers).
  * Aggregates total minutes in memory during execution and outputs a progress summary on demand.
  * Terminates cleanly when the user selects the Exit option.

---

## 2. IPO Chart (Input - Process - Output)

| Input | Processing | Output |
| :--- | :--- | :--- |
| • `main_choice` (Integer: 1–4)<br>• `sub_choice` (Integer: 1–3)<br>• `duration` (Real / Integer: $\ge 0$) | 1. Initialize `total_cardio = 0`, `total_strength = 0`.<br>2. Loop main menu display until user enters `4`.<br>3. Validate that `main_choice` is between 1 and 4.<br>4. If `1` (Cardio) or `2` (Strength):<br>&emsp;a. Display respective submenu.<br>&emsp;b. Validate `sub_choice` is between 1 and 3.<br>&emsp;c. Prompt for duration; loop until `duration >= 0`.<br>&emsp;d. Map choice to activity name.<br>&emsp;e. Add `duration` to running total.<br>5. If `3` (Summary):<br>&emsp;a. Calculate `total_active = total_cardio + total_strength`.<br>&emsp;b. Determine goal achievement status ($>= 120$ min).<br>&emsp;c. Display formatted summary report.<br>6. If `4` (Exit): Display exit farewell and terminate. | • Invalid input warning messages<br>• Success confirmation of logged minutes and activity name<br>• Formatted Activity Summary:<br>&emsp;- Total Cardio Minutes<br>&emsp;- Total Strength Minutes<br>&emsp;- Total Active Minutes<br>&emsp;- Weekly Goal Status Message<br>• Exit farewell message |

---

