
## Preventing SQL Injection When Coding - Parameterized Queries
*By Logan Limbaugh*

<ins>Overview</ins><br>
Parameterized Queries are a common practice to preventing SQL Injection. This is achieved through seperating user inputs from the SQL queries through prepared statements or parameterized queries! Below I will show you an example of basic, injectable code, as well as a quick fix on how to prevent SQL injection!

For the purpose of this guide, all examples will be given in Python.

---

<ins>Vulnerable Code</ins><br>
The code below is vulnerable to SQL injection as it directly takes the user input and places it within the query. For this code, assume that the user_input variable is collected from a form, and the SQL code is the code designed to process their search with the database.<br>


    user_input = "Decorations'; DROP TABLE Products; --"
	query = f"SELECT ProductName, ProductDesc, Price FROM Products WHERE ItemName = '{user_input}'"
	cursor.execute(query)

This code is vulnerable to injection as it would create a query that looks like this, succesfully injecting into the database and deleting the table "Products".<br>

    SELECT ProductName, ProductDesc, Price FROM Products WHERE ItemName = 'Decorations'; DROP TABLE Products; --'
    
---

<ins>Parameterized Code</ins><br>
To fix this code, we can easily adjust how the user_input is being passed to the query through parameterization! With the code below we are using the character ? to handle the user input, which essentially is taking the input and parameterizing it. The user input will be rendered as a string for the purpose of the SQL query instead of readable code.<br>

    user_input = "Decorations'; DROP TABLE Products; --"
    query = "SELECT ProductName, ProductDesc, Price FROM Products WHERE ItemName = ?"
	cursor.execute(query, (user_input,))

This code would generate an SQL statement that is no longer malicious.<br>

    SELECT ProductName, ProductDesc, Price FROM Products WHERE ItemName = 'Decorations''; DROP TABLE Products; --'

---

Return to the Main Page -> [Here](https://github.com/Loganhl/SQL-Injection-Prevention/blob/main/README.md)

