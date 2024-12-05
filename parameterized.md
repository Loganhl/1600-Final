## Preventing SQL Injection When Coding - Parameterized Queries
*By Logan Limbaugh*

<ins>Overview</ins><br>
Parameterized Queries are a common practice to preventing SQL Injection. This is achieved through seperating user inputs from the SQL queries through prepared statements or parameterized queries! Below I will show you an example of basic, injectable code, as well as a quick fix on how to prevent SQL injection!

---
<ins>Vulnerable Code</ins><br>
The code below is vulnerable to SQL injection as it directly takes the user input and places it within the query. For this code, assume that the user_input variable is collected from a form, and the SQL code is the code designed to process their search with the database.

