## Preventing SQL Injection When Coding
*By Logan Limbaugh*

<ins>Overview</ins><br>

This is a comprehensive guide on techniques and practice to prevent your databases from SQL Injection, a highly common method of cyber attacks that can steal, manipulate, and destroy data.

The target audience for this guide are beginning developers who wish to understand SQL injection and it's effects as well as ways to prevent it!

---
<ins>What is SQL Injection</ins><br>

SQL Injection is a type of cyber attack that involves the user taking advantage of vulnerabilities in code or in databases to edit, steal, or destroy data within the database. This attack is often performed through users inserting SQL queries into input fields within code. For example when a user is prompted with an input field within an application to search for something, they may enter "Decorations" resulting in a query like this:

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
