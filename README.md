## 3 Easy Ways to Prevent SQL Injection When Coding
*By Logan Limbaugh*

_###Overview_<br>

This is a comprehensive guide on techniques and practice to prevent your databases from SQL Injection, a highly common method of cyber attacks that can steal, manipulate, and destroy data.

The target audience for this guide are developers who have a general or beginning understanding of SQL database management, SQL Queries, and programming who wish to understand SQL injection and it's effects as well as ways to prevent it!

---
<ins>What is SQL Injection</ins><br>

SQL Injection is a type of cyber attack that involves the user taking advantage of vulnerabilities in code or in databases to edit, steal, or destroy data within the database. This attack is often performed through users inserting SQL queries into input fields within code. For example when a user is prompted with an input field within an application to search for something, they may enter "Decorations" resulting in a query being sent to the database that looks like this:

    SELECT ProductName, ProductDesc, Price
    FROM Products
    WHERE ItemName LIKE "%Decorations%"

This would likely return to the user all of the products which Decorations within their name. However with SQL Injection, someone may input something like this into the search:

    Decorations'; SELECT UserNames, CardInfo FROM Orders; --

An unchecked program would register this query as a normal creating a statement like this to query the database:

    SELECT ProductName, ProductDesc, Price 
    FROM Products 
    WHERE ItemName LIKE "%Decorations%"; 
    SELECT UserNames, CardInfo 
    FROM Orders; --
    
In this scenario, this injection attack would return the attacker information regarding users within the database as well as their private card info, which can be devastating for not only the company using this code, but the consumers within their databases as well. This is only a simply example of what SQL Injection is capable of, however it's possibilities are much greater than what is showed above. For example attackers can input blank queries returning error messages, attaching unions to queries, or even making DNS requests.

---
<ins>How to Prevent Injection</ins><br>

Now that you know a basis of SQL Injection, let's look into ways that we can prevent our databases and frameworks from being easily infiltrated. Below you will find three different methods of Injection Prevention, with attached markdown pages going further in-depth.

**Parameterized Queries (Prepared Statements)**
Parameterized Queries are a common practice to preventing SQL Injection. This is achieved through seperating user inputs from the SQL queries through prepared statements or parameterized queries! In the page below I will show you examples of how to accomplish this.<br>

[Parameterized Queries Example](https://github.com/Loganhl/SQL-Injection-Prevention/blob/main/parameterized.md)

**Input Validation**
Validating a users input is a simple and effective way of preventing SQL Injection. This is through creating a system of filtration that is used to check user input before it is sent further into the code to be processed. <br>

[Input Validation Example](https://github.com/Loganhl/SQL-Injection-Prevention/blob/main/validation.md)

**Input Escaping**
Very similar to Input Validation, Input Escaping is filtering specific characters within an input and changing them so that we can prevent SQL Injection.<br>

[Input Escaping Example](https://github.com/Loganhl/SQL-Injection-Prevention/blob/main/escape.md)

---

<ins>Conclusion</ins><br>

Thanks for making your way through the guide! To take advantage of what you have learned here keep these simple, yet highly effective techniques in mind when working with user inputs and SQL databases! Whilst these are not the only effective measures, I encourage you to seek out other methods of securing your code and practicing programming with cybersecurity in mind!
