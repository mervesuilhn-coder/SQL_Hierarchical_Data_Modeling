# SQL_Hierarchical_Data_Modeling
I created this dedicated space to prove my proficiency in one of the most challenging areas of SQL development. Handling hierarchies requires a deep understanding of logical recursion and data integrity, and these scripts represent my journey in mastering those complex structures
# SQL_Hierarchical_Data_Modeling
A specialized collection of SQL scripts focusing on hierarchical data structures, recursive queries, and parent-child relationships within relational databases.
"I established the fundamental recursive structure to map out employee-manager relationships. 
By starting with the root manager  and iteratively joining employees to their supervisors, I successfully generated a full hierarchical path for each record."
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
FILE :
https://github.com/mervesuilhn-coder/SQL-Hierarchical-Data-Modeling/blob/3e980af55df0365e81c16a8df10011e0d86105b8/scripts/Hierarchy_Create_Table

Description:First, I created a sample employee table with a top manager to create a hierarchy.
-----------------------------------
FILE:
https://github.com/mervesuilhn-coder/SQL-Hierarchical-Data-Modeling/blob/b2997c5ffcc7bad8631a1fb7d64d1b002c926b21/scripts/Based_Hierarchy.sql

Description:
I implemented a Recursive CTE to navigate and visualize a hierarchical organizational structure. My approach followed a two-step logical process:

Establishing the Anchor: I first identified the root of the hierarchy by selecting the top-level manager who does not report to anyone else.

Defining the Recursion: I then used a recursive join to link each employee to their respective manager. During this process, I dynamically constructed a 'Hierarchy Path' (e.g., Jan > Michael > Dwight) by casting the employee names into a string and appending them at each level of the tree.

Result: This allowed me to transform a simple parent-child table into a comprehensive, sorted reporting map that clearly shows the entire chain of command within the organization.
------------------------------
FILE:
https://github.com/mervesuilhn-coder/SQL-Hierarchical-Data-Modeling/blob/214f9ff423e2187379eead480b67e9769682ff3e/scripts/Recursive_CTE_Hierarchy.sql

Description:
1.
I initiated the recursion to map out every employee's position.
By starting with the top-level executive (managerAD IS NULL), I iteratively built a string-based path (HiyerarsiYolu) to visualize the chain of command for every node.
2.
I calculated the 'Direct Report' count for every manager.
I grouped the raw employees table by manager ID to find exactly how many people report directly to each supervisor, ensuring I excluded null entries to maintain data accuracy.
3.
I merged the hierarchy paths with the report counts.
 Using a LEFT JOIN and COALESCE, I ensured that even 'Leaf Nodes' (employees who aren't managers) are included in the report with a value of 0 instead of NULL.
4.
I implemented a Self-Join using a Pattern Matching (LIKE) condition.
This is the most critical part of my analysis. By joining the table back to itself where the employee's path starts with the manager's path (LIKE CONCAT(m.HiyerarsiYolu, '%'))
I was able to list not just direct subordinates, but every single person under a specific manager's entire lineage.

