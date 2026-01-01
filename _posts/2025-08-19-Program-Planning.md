PA1: Program Planning
	Pseudocode and flowcharts allow stakeholders from technical and non-technical backgrounds alike to understand and explain an algorithm of a program. Pseudocode provides a step-by-step explanation of an algorithm using plain English in a code-like structure (Geeksforgeeks.org, 2025). Flowcharts present the pictorial representation of the flow of an algorithm. These two core concepts are required components of documentation in programming. 
A. Flowchart (see other attachment)
B. Pseudocode
START
IMPORT data from “D598 Data Set” as df
CHECK for duplicate rows in df
	IF duplicate rows exist THEN
		delete duplicates and store as df2
	ELSE 
store df as df2
GROUP each ‘Business ID' by 'Business State'
RUN descriptive statistics (mean, median, min, and max) for all numeric variables by ‘Business State’
STORE this result as df3
FILTER df3 to identify ‘Business ID’ with negative debt-to-equity (DE) ratios
	IF negative DE THEN 
		store as df4
	ELSE
		leave in df3
CREATE df5 to provide the debt-to-income ratio for each ‘Business ID’ (DI = ‘Long-term Debt’/’Total Revenue’) 
CONCATENATE this df5 to the original data frame
END
C. The Relationship Between the Flowchart and Pseudocode 
1. The Logic of Pseudocode and Flowcharts
Pseudocode
Pseudocode focuses on logic rather than syntax, helps identify logical errors before coding, improves team communication, and provides documentation for coding. Pseudocode serves as a universal language for teams. This type of documentation allows team members to think through and understand the steps of the algorithm systematically before it is entered into their programming language of choice. (Codecademy Team, 2025)
Pseudocode best practices:
•	Understand the problem
•	Use simple language
•	Be consistent
•	Use proper structure
•	Include all necessary steps
•	Use clear names
•	Comment your code
•	Test your pseudocode
(WGU, Lesson 2: Pseudocode)


Flowcharts 
Flowcharts utilize different shapes that are connected by arrows for different steps in the coding process. The standard flowchart symbols are as follows: 
•	Start/End Symbol – represented by an oval that shows the start or end of a process
•	Input/Output Symbol – represented by a parallelogram, shows the materials or information entering or leaving a process
•	Action or Process Symbol - represented by a rectangle, shows a specific process, action, or function
•	Decision Symbol – represented by a diamond, shows a decision point. (WGU module 2.1) 
Flowcharts enable stakeholders to think through decisions and choices with planning, communication, analysis, debugging, and documentation. (WGU, Lesson 1: Flowcharts).
2. The Alignment Between Pseudocode and Flowcharts.

Pseudocode is written in a text-based format that is best for detailed logic, has a lower learning curve that is written to technical audiences, and is space-efficient. Whereas a flowchart has a visual diagram format that is best for complex decision trees, has a moderate learning curve, is written for mixed audiences, and requires more space than text-based pseudocode (Codecademy, 2025). Additionally, flowcharts are good for documenting instructions and explanations, while pseudocode is better suited for the purpose of human understanding (Geeksforgeeks, 2025).


Pseudocode START
Step 1: Import data from "D598 Data Set" as df Step 2: Check for duplicate rows in df
IF duplicates exist THEN

Delete duplicates and store df as df2
 
Flowchart START
Import data from "D598 Data Set" and store as df Check if duplicate rows exist? Remove duplicates


Yes --> duplicates and store df as df2
 

 
ELSE
 


Store original df as df2
 


No --> store as df2
 

 
Step 3: Group each 'Business ID' by 'Business State'

Step 4: Run descriptive statistics (mean, median, min, and max) for all numeric variables by 'Business State'

Step 5: Store as df3

Step 5: Filter df2 to identify 'Business ID' with negative debt-to-equity (DE) ratios
IF negative DE THEN Include in new df4
 
Group 'Business ID' by 'Business State'

Run descriptive stats for all numerical variables by 'Business State'

        Store as df3

Filter df2 to identify 'Business ID' with negative debt-to-equity (DE) ratios



Yes --> Include in new df4
 
ELSE
 


Leave in df2
 


No --> leave in df2
 

Step 6: Create df5 to provide debt-to-income ratio for each ‘Business ID’ (DI = 'Long- term Debt'/'Total Revenue') 

Step 7: Concatenate df5 to df2 and store as df5
 END
 
Create df5 to provide debt-to-income ratio ‘DI_Ratio’ for each 'Business ID'

Concatenate df5 to df2 and store as df5
END
 

As seen above, the Pseudocode and data within the flowchart symbols outline the code structure. Effective flowcharts create better readability and streamline development for pseudocode, thus ensuring efficient problem solving, clarity, and efficiency in programming languages such as Python and R. Pseudocode serves as a crucial programming tool, a blueprint that bridges human understanding with computer program execution. (WGU, Section 2: Summary)

References
Codecademy Team. (Accessed August 16, 2025). Psuedocode and Flowchart: Complete Beginner’s Guide.
Geeksforgeeks.org. (2025, July 26). What is PseudoCode: A Complete Tutorial.
Western Governors University (Accessed August 16, 2025). D598 Analytics Programming Core Concepts: Documenting Required Components – Lesson 1: Flowcharts.
Western Governors University (Accessed August 16, 2025). D598 Analytics Programming Core Concepts: Documenting Required Components – Lesson 2: Pseudocode.
Western Governors University (Accessed August 16, 2025). D598 Analytics Programming Core Concepts: Documenting Required Components – Section 2: Introduction.
Western Governors University (Accessed August 16, 2025). D598 Analytics Programming Core Concepts: Documenting Required Components – Section 2: Summary.
<img width="468" height="618" alt="image" src="https://github.com/user-attachments/assets/67a91170-2867-4582-b48c-5e4409872a5c" />
