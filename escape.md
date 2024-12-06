## Preventing SQL Injection When Coding - Input Escaping
*By Logan Limbaugh*

### <ins>Overview</ins><br>
Input escaping is the process of filtering  through a users input to change specific characters commonly used in injection, in this case ' and ". 
--- 

### <ins>Vulnerable Code</ins><br>
The code below is vulnerable to SQL injection as it directly takes the user input and places it within the query. For this code, assume that the user_input variable is collected from a form, and the SQL code is the code designed to process their search with the database.<br>


    user_input = "Decorations'; DROP TABLE Products; --"
	query = f"SELECT ProductName, ProductDesc, Price FROM Products WHERE ItemName = '{user_input}'"
	cursor.execute(query)

This code is vulnerable to injection as it would create a query that looks like this, succesfully injecting into the database and deleting the table "Products".<br>

    SELECT ProductName, ProductDesc, Price FROM Products WHERE ItemName = 'Decorations'; DROP TABLE Products; --'
    
---

### <ins>Code with Input Validation</ins><br>
To add input escaping into our code, we want to filter through the user input and change injection characters such as ' or " to be replaced with double of their initial value. I have also included parameterization, which we learned in the previous guide!
	
	user_input = "Decorations'; DROP TABLE Products; --" 

	def escape_input(user_input): 
		return user_input.replace("'", "''")
			
	user_input = escape_input(user_input)
	query = "SELECT ProductName, ProductDesc, Price FROM Products WHERE ItemName = ?"
	cursor.execute(query, (user_input,)) 

---

#### Return to the Main Page -> [Here](https://github.com/Loganhl/SQL-Injection-Prevention/blob/main/README.md)
