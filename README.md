# fitness-tracker-design
Fitness Tracker Pseudocode and Flowchart and IPO Chart

# Software Design: Campus Fitness & Activity Tracker

**Course:** Software Design & Logic  
**Author:** ITP 150 Student  
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

## 3. Pseudocode

```
MODULE Main()
    DECLARE Integer total_cardio = 0
    DECLARE Integer total_strength = 0
    DECLARE Integer total_active = 0
    DECLARE String main_choice = ""  
    DECLARE String sub_choice = ""
    DECLARE Real duration = 0.0  
    DECLARE String activity_name = ""

    DISPLAY "=============================="  
    DISPLAY "     CAMPUS FITNESS TRACKER   "  
    DISPLAY "=============================="  

    WHILE True  
        // Step 1: Main Menu & Input Validation  
        DISPLAY "---MAIN MENU---"
        DISPLAY "1. Log Cardio Workout"
        DISPLAY "2. Log Strength Workout"
        DISPLAY "3. View Activity Summary"
        DISPLAY "4. Exit"
        DISPLAY "Enter your choice (1-4):"
        INPUT main_choice

        WHILE main_choice != 1 AND main_choice != 2 AND main_choice != 3 AND main_choice != 4
            DISPLAY "Invalid. Choice must be 1, 2, 3, or 4. Try Again:"
            INPUT main_choice
        END WHILE

        // Step 2: Route Submenus and Actions
        IF main_choice == 1 THEN
            DISPLAY "--- CARDIO MENU ---"
            DISPLAY "1. Running / Jogging"
            DISPLAY "2. Cycling"
            DISPLAY "3. Swimming"
            DISPLAY "Enter cardio activity (1-3):"
            INPUT sub_choice

            WHILE sub_choice != 1 AND sub_choice != 2 AND sub_choice !=3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                activity_name = "Running / Jogging"
            ELSE IF sub_choice == 2 THEN
                activity_name = "Cycling"
            ELSE
                activity_name = "Swimming"
            END IF

            DISPLAY "Enter duration in minutes:"
            INPUT duration
            WHILE duration < 0
                DISPLAY "Invalid. Please enter minutes >= 0:"
                INPUT duration
            END WHILE

            total_cardio = total_cardio + duration
            DISPLAY "Successfully added ", duration, "minutes for ", activity_name, "."

        ELSE IF main_choice == 2 THEN
            DISPLAY "--- STRENGTH MENU ---"
            DISPLAY "1. Upper Body"
            DISPLAY "2. Lower Body"
            DISPLAY "3. Core & Flexibility"
            DISPLAY "Enter strength category (1-3):"

            WHILE sub_choice != 1 AND sub_choice != 2 AND sub_choice !=3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT sub_choice
            END WHILE

            IF sub_choice == 1 THEN
                activity_name = "Upper Body"
            ELSE IF sub_choice == 2 THEN
                activity_name = "Lower Body"
            ELSE
                activity_name = "Core & Flexibility"
            END IF

            DISPLAY "Enter duration in minutes:"
            INPUT duration
            WHILE duration < 0
                DISPLAY "Invalid. Please enter minutes >= 0:"
                INPUT duration
            END WHILE

            total_strength = total_strength + duration
            DISPLAY "Successfully added ", duration, "minutes for ", activity_name, "."

       ELSE IF main_choice == 3 THEN
           total_active = total_cardio + total_strength
           DISPLAY "=========================================="
           DISPLAY "          ACTIVITY SUMMARY                "           
           DISPLAY "=========================================="
           DISPLAY "Total Cardio:", total_cardio  
           DISPLAY "Total Strength:", total_strength
           DISPLAY "Total Active:", total_active

           IF total_active >= 120 THEN
               DISPLAY "Status: Goal achieved! You exceeded 120 weekly active minutes."
           ELSE IF total_active > 0 THEN
               DISPLAY "Status: Keep Going! ", (120 - total_active), " more minutes needed to hit"
               DISPLAY "your weekly target."
           ELSE
               DISPLAY "Status: No workouts logged yet."
           END IF
           DISPLY "=========================================="
       ELSE IF main_choice == 4 THEN
           DISPLAY "Thank you for using Campus Fitness Tracker. Stay Active!"
           BREAK
       END IF
    END WHILE
END MODULE

```

    

    
