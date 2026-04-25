# BRT-practiclas-phThis is a professional narrative you can copy and paste directly into your GitHub `README.md` file. It frames your journey from the technical glitches to the final, high-level solutions.

---

# SQL Practical Portfolio: Fundamentals to Advanced Analytics

## Project Overview & Intent
This repository documents a comprehensive deep-dive into SQL, transitioning from foundational queries to advanced analytical structures. The project was executed using **Databricks (Spark SQL)** on a retail dataset consisting of 1,000 transactions. 

The primary goal was to transform raw data into actionable business insights while mastering the nuances of database logic, syntax strictness, and data granularity.

## Portfolio Components
* **Digital Practical Assessments:** Two sets of comprehensive SQL scripts testing data filtering, aggregation, and complex logic.
* **Handwritten Coding Exercises:** Scanned documentation of my conceptual coding process, showcasing logic development before implementation.
* **Academic Foundation:** A collection of 20 detailed class lessons and notes that served as the roadmap for this practical application.

---

## Technical Narrative: Challenges & Remedial Actions
While the majority of the code executed successfully on the first attempt, the transition into the Databricks environment revealed three specific "glitches." These served as critical learning moments for my development as a data analyst.

### 1. The Granularity Glitch (Distinct vs. Unique IDs)
* **The Issue:** My initial attempt to view unique product categories returned 1,000 rows instead of three. I realized that by including the `Transaction ID` in a `DISTINCT` query, the database treated every row as unique due to the ID, even if the category was the same.
* **Remedial Action:** I learned to decouple unique identifiers from categorical lists. To view independent lists side-by-side without them "multiplying" each other, I implemented a `ROW_NUMBER()` and `FULL OUTER JOIN` strategy to create a clean, dictionary-style view.

### 2. The Operator Syntax Glitch (Logical "OR" & "BETWEEN")
* **The Issue:** Coming from a natural language perspective, I initially omitted explicit equality signs when using `OR` and `BETWEEN` for text strings. Databricks rejected the code because it requires a strict "Column + Operator + Value" structure for every condition.
* **Remedial Action:** I transitioned to using the `IN` operator. This not only fixed the syntax errors but also created cleaner, more readable code that is easier to maintain when filtering multiple categories like 'Beauty' and 'Electronics'.

### 3. The "IS NOT" vs. Symbol Inequality Glitch
* **The Issue:** I attempted to exclude categories using the phrase `IS NOT 'Clothing'`. Databricks refused this, as `IS NOT` is a specialized operator reserved strictly for `NULL` (empty) states.
* **Remedial Action:** I corrected this by using the mathematical inequality symbols (`!=` or `<>`). This clarified the distinction between checking a "Value" (text) versus checking a "State" (nothingness).

---

## Points of Observation
* **Mathematical Symbols in Text Logic:** A key takeaway was the integration of mathematical operators (`>`, `<`, `!=`) to perform logical tests on string data.
* **The "Having" Constraint:** During the final "Big Code" consolidation, I observed that the `HAVING` clause cannot be used in a master list without a `GROUP BY`. 
* **The Wrapper Solution:** To circumvent the `HAVING` limitation, I utilized a **Subquery Wrapper**. This allowed me to calculate advanced window functions (like Category Revenue Totals) and filter them in one single execution without losing the 1,000 rows of individual transaction detail.

## Conclusion
This project demonstrates more than just coding ability; it demonstrates the ability to troubleshoot platform-specific glitches and architect "Master Queries" that balance high-level summaries with granular data. The result is a robust, error-free analytical toolset.
