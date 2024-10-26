<h1>Website SQL injection</h1>

<h2>Description</h2>
This project was done as one of the CTF challenges in Hack the Boo halloween event on Hack the Box. The goal was to find the SQL injetion vulnerability in website and then use it to obtain list of tables in website's Database and retrieve data from the 
tabel containing the flag. For some basic notes on the SQL injection you can visit my blog post <a href="https://lukesdevsecopsnotes.blogspot.com/search/label/sql-injection">here</a>
<br />


<h2>Languages and Utilities Used</h2>

- <b>SQL</b>

<h2>Project walk-through:</h2>

After visiting the website I have verified the empty searh to see how the SQL query is formed:
<p align="center">
<img src="https://github.com/user-attachments/assets/f91791ba-360e-4b61-9bab-6b533083630d" height="80%" width="80%" alt="PHP code injection"/></p>
<br />
<br />
The next step was to check if there is a possibility of SQL injection by adding the origin column into filter:
<p align="center">
<img src="https://github.com/user-attachments/assets/22780de5-ef97-4e86-aef7-46e4f7856b8a" height="80%" width="80%" alt="PHP code injection"/></p>
<br />
<br />
After confirming SQL injection is possible I tried to add a union select from information_schema to get list of tables that have column with word "flag" in the name:
<p align="center">
<img src="https://github.com/user-attachments/assets/461bb53d-99fa-4684-99d6-38ac8d043996" height="80%" width="80%" alt="encoded powershell script"/></p>
<br />
<br />
The query revealed that there in fact is a table called "flag" that contains column "Flag"
<p align="center">
<img src="https://github.com/user-attachments/assets/296e2fbb-05e0-4cea-b234-784ee088fe54" height="80%" width="80%" alt="encoded powershell script"/></p>
<br />
<br />
The next step was to simply add a union select to table "Flag" to get the desired value:
<p align="center">
<img src="https://github.com/user-attachments/assets/bd744743-9f79-4df7-9be9-e1f623807af2" height="80%" width="80%" alt="encoded powershell script"/></p>


