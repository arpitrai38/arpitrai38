//Database Session Dated 10/06/2026//


Use of create cmd to create a new db :-


//Syntax :-

          create database <database name>;


          //E.g.-

                   create database fdb3;



Table:-  Table is a  collection of rows and column.


  //Another name of Rows and Columns//

    Rows = Tuples , Relation.

    Columns = Attribute.


  // Use of Create cmd to create a new Table//


     Syntax :-

           create table <table_name>
           (
             <column_name_1> <data_type>,
             <column_name_3> <data_type>,
             <column_name_3> <data_type>
            );
 
      E.g.:-

           Primary Key :-  Primary Key is a field in a table .Which is used to identify each record uniquely, it is atomic and not null.

           create table employee
 
                                (
                                   empid int primary key,
                                   empname varchar(50),
                                   salary bigint
                                 );
 

           //How to insert record into a Table.

 
                 Use of insert cmd to insert record into table:-


                      Syntax :-

                                 insert into <table_name> values(<value1>, <value2>, <value3>);

 
                                 E.g =>
                                         insert into employee values( 1001 , 'Arpit' , 1500000);
                                         insert into employee values( 1002 , 'Mohit' , 55000);
                                         insert into employee values( 1003 , 'Rachit' , 660000);
 

 //Use of insert cmd to insert multiple records in tables :-


        E.g.
              insert into employee values(1004, 'Mudit',500000),(1005,'Sobhit',50000);



 \\ use of select cmd to select rec from table :-


         1.select all column along with all rows.
 
           select * from employee;

         2.select specific column along with all rows.
 
           select empid , empname from employee ;
 
         3.select specific rows (filtering) with all column.
             // where clause := used to specify condition in sql statement.

               select * from employee where (empid = 1001);
 
         4.select specific rows with specific column.
 
           E.g. => select empid ,empname columns from employee table for empid 1001.
 
                // select empid , empname from employee where (empid = 1001);


// Use of delete cmd to delete record from table.

Syntax :-
         delete from <table name> where <condition>;
 
        E.g.=>
               delete from employee where empid = 1001;







                                         Database  Session 2   11/06/2026


Update command


Use of update command to modify record of table
Syntax:=
update <table_name> set <column1>=<value1>,<column2>=<value2> where <condition>;


update employee set empname = "Ankit" , salary = 100000 where empid = 1002;




//Trucate command//



Syntax :-

truncate table <table_name>;


E.g. =>  truncate table employee;




//Drop command

Syntax =>
drop table <table_name>;

E.g.=>
drop table employee;


create table login(
userid varchar(50) primary key,
password varchar(50)
);



//Alter command

Alter = Used to modify the structure of Database obj.



Syntax =>

alter table <table_name> <operation> <column_name> <data_type>;

ADD

alter table <table_name> add <column_name> <data_type>;

E.g=>

       alter table login add (user_name varchar(50));

DROP
 
       ALTER TABLE <TABLE_NAME> DROP COLUMN <COLUMN_NAME>;
E.g=>

      ALTER TABLE login DROP user_name;

MODIFY datatype

       alter table <table_name> modify <column_name> <datatype>


E.g=> alter table login modify password varchar(60);



RENAME a COLUMN
 
       alter table <table_name> change <column_oldname>  <new_name> <datatype>

E.g =>
         alter table login change password  psswd  varchar(50);


USE OF ALTER COMMAND TO ADD A NEW COLUMN AFTER GIVEN COLUMN.

       alter table <table_name> add <column_name> <data_type> after <given_column_name>;

E.g => alter table login add username varchar(50) after userid;



USE OF ALTER COMMAND TO ADD A NEW COLUMN AS FIRST COLUMN.
 
       alter table <table_name> add <column_name> <datatype> first;

E.g=> alter table login add s_no int first;


USE OF ALTER COMMAND TO DROP PRIMARY KEY OF THE GIVEN COLUMN

      alter table <table_name> drop primary key;
E.g. =>

USE OF ALTER COMMAND TO ADD A NEW COLUMN WITH PRIMARY KEY AT FIRST POSITION.

     alter table <table_name> add <column_name> <datatype> primary key first;
E.g.=> alter table login add e_no int primary key first;




alter table login add primary key(user_name);

                            Session 3 Dated 12/06/2026

Join operation =>
                  If you want to select data from two or more table then you can perform join operation.
               For join operation atleast on column should be common in both tables.


Table Name employee

Column name| Dat type | constraint
empid         int        p.k
empname       varchar(50)|


Table Name product

Column|  Data type | constraint

pid       int         P.K
pname     VARCHAR(50)
empname   int         F.K



FOREIGN KEY:- it is a field in a table which works as p.k in another table. it is used to establish relationship btw  2 table.  In a single table there in more than 1 foreign key.


Create table employee(
empid int primary key,
empname varchar(50));



CREATE TABLE product (
    pid int PRIMARY key,
    pname varchar(50),
    empid int, FOREIGN KEY(empid) REFERENCES employee(empid)
);

Table Name => employee

empid | empname

1001    John
1002    Brown
1003    Green
1004    Lily

Table Name => product

pid | pname  |  empid
101 | printer|   1001
102 | scanner|   1002
103 | plotter|   1002
104 | laptop |   1003
105 |projector| NULL

//value in employee table

INSERT INTO employee VALUES(1001,"John"),(1002,"Brown"),(1003,"Green"),(1004,"Lily");

//value in product table


INSERT INTO product VALUES ( 101,"Printer",1001 ),(102 ,"Scanner",1002),(103,"plotter",1002),(104,"Laptop",1003),(105,"projector", NULL);




insert into <table_name> (<column1>,<column2>) values (<value1> <value2>);

E.g=> insert into product(pid,pname) values(105,"projector");



Natural join operation =>
                          When you perform natural join operation then common record of both table is displayed.


select employee.empname ,product.pname from employee,product where employee.empid = product.empid;



Left join operation =>
                      When you perform left join operation then all records of left table are displayed and mATCHING RECORDS OF RIGHT TABLE ARE DISPLAYED.


E.g. =>
          select employee.empname,product.pname from employee left join product  on employee.empid = product.empid;


Right join operation =>When you perform right join operation then all records of right table are displayed and mATCHING RECORDS OF left TABLE ARE DISPLAYED.

E.g=>   select employee.empname,product.pname from employee left join product  on employee.empid = product.empid;

 

                                        session 4          Dated :- 14/06/2026




Full join operation =>  Acess all record from table. Basically full join operation is the union of left join and right join.


syntax =>
          Select employee.ename,product.pname from employee left join product on employee.empid = product.empid union select employee.ename , product.pname from employee right join product on  employee.empid = product.empid

 




SQL FUNCTION =>   In SQL there are many built in function which are used for data analysis. These function are also called aggregate functions. These function can be used with select command only.


create table empinfo(
empid int primary key,
empname varchar(50),
salary bigint
);



INSERT INTO empinfo VALUES (1001,"Ajay",80000),(102,"vijay",60000),(1003,"Sanjay",75000),(1004,"Arpit",70000);




COUNT() => Count function is used to count no of rows of table.

select count(*) from empinfo;

SUM() => Sum function is used to find sum of values of given numerical.

select sum(salary)"Total Salary" of empinfo;


MAX()=> Max() function is used to find max value of given numerical.

select max(salary)"Max Salary" of empinfo;

MIN()=> Min function is used used to find min value of given numeric column.

select min(salary)"Min Salary" from empinfo;

AVG()=> Avg function iS used to find average value of given column.


select avg(salary)"Average Salary" from empinfo;



UPPER()=> Upper function is used to convert varchar type value into upper case.

Select upper(empname) from empinfo;

LOWER()=>Lower function is used to convert varchar type value into lower case.

Select lower(empname) from empinfo;


ORDER BY:= Used to arrange record in ascending or descending order.


Show record of empinfo table with increasing value of salary.
 
    select * from empinfo order by salary;

2.Show record of empinfo table with decreasing value of salary.

   select * from empinfo order by salary DESC;

*******************************************************************

Task 1=> Show record of empinfo table with maximum salary.

 
         select * from empinfo where salary = (select max(salary) from empinfo);


Task 2=> Show record of empinfo table with  second max salary.


         select * from empinfo where salary= (select max(salary) from empinfo where salary< (select max(salary) from empinfo));


Task 3=> Show record of empinfo table with third maximum salary.


                            session :- 5 Dated 15/06/2026



1. Show records of 'male' patient from 'southwest' region.
select * from insurance where gender ="male"and region = "southwest";


2. Show all records having bmi in range 30 to 45 both inclusive.
select * from insurance where bmi > 30 and bmi<45;
select * from insurance where bmi between 30 and 45;

3. Show minimum and maximum bloodpressure of diabetic patient who smokes. Make column names as MinBP and MaxBP respectively.

select min(bloodpressure) as MinBP , max(bloodpressure) as MaxBP from insurance  where smoker = "yes" and diabetic = "yes";


4. Find no of unique patients who are not from southwest region.

 select distinct count(*)"No of Patient" from insurance where region <>"southwest";


5. Total claim amount from male smoker.

select sum(claim) as "Total Claim" from insurance where gender = "male" and smoker = "yes";


6. Select all records of south region.
select * from insurance where region like "south%" ;


7. No of patient having normal blood pressure. Normal range[90-120]

select count(*) as "No. of Patients" from insurance where bloodpressure between 90 and 120;


8. What is the average claim amount for non-smoking female patients who are diabetic?

select avg(claim)"Average claim" from insurance where gender = female and smoker = "no" and diabetic = "yes"  ;


9. Write a SQL query to delete all records for patients who are smokers and have no children.


delete from insurance where smoker= "yes" and children = 0;



1=>
    create table issuebook(issueid int primary key, bookid varchar(15), FOREIGN    KEY(bookid) references  bookstore(bookid),studentname varchar(50),bookname varchar(100),authorname varchar(100));



2=>  INSERT INTO issuebook values(1,"TMU1",1001,"Rajat Singh","Let us C","Y.P.kanetkar"),(2,"TMU4",1001,"Rajat Singh","Effective java","Joshua Bloch"),(3,"TMU2",1002,"Dinesh Singh","Let us C","Y.P.kanetkar"),(4,"TMU5",1003,"Rajat Singh","Effective java","joshua Bloch");



3=>   select issuebook.bookid , bookstore.isbnno,issuebook.rollno, issuebook.studentname, issuebook.bookname,issuebook.authorname FROM bookstore,issuebook where bookstore.bookid =  issuebook.bookid ;



4=>   select issuebook.bookid , bookstore.isbnno,issuebook.rollno, issuebook.studentname, issuebook.bookname,issuebook.authorname from bookstore left join issuebook on bookstore.bookid = issuebook.bookid union select issuebook.bookid , bookstore.isbnno,issuebook.rollno, issuebook.studentname, issuebook.bookname,issuebook.authorname from bookstore RIGHT join issuebook on bookstore.bookid = issuebook.bookid;

 

                       DBMS     Dated=>16/06/2026

1 create database practicedb ;
 
      create table userinfo(FirstName varchar(30),LastName varchar(30),contactno varchar(15) primary key, Emailadress varchar(50));

Alter table userinfo add gender varchar(6) after Lastname;




2.GIVEN DATA

 "Brijesh", "Mishra", "Male", "9453318798", "brijesh@gmail.com"
"Rajat "Verma", "Male", "9936652039", "rajat@gmail.com"
"Nisha" "Singh" ,"Female" ,"9559763249" ,"nisha@gmail.com"
"Priya" , "Singh", "Female" ,"7753001621", "priya@gmail.com"

Query=>

        insert into userinfo value("Brijesh", "Mishra", "Male", "9453318798", "brijesh@gmail.com"),
("Rajat", "Verma", "Male", "9936652039", "rajat@gmail.com"
),("Nisha", "Singh" ,"Female" ,"9559763249" ,"nisha@gmail.com"
),("Priya" , "Singh", "Female" ,"7753001621", "priya@gmail.com"
);

3=>i) Select * from userinfo;
 
   ii) select Firstname,LastName,Emailaddress from userinfo;

iii) select * from userinfo where contactno = "9453318798";

iv)  select * from userinfo where gender="male";

v) select count(*)"No. of Female" FROM userinfo WHERE gender = "Female" ;
 brijesh.225409@gmail.com’ for contactno 9453318798.

vi) update userinfo set Emailadress = "brijesh.225409@gmail.com" where contactno = "9453318798";

vii) delete from userinfo where contactno = "9453318798";

viii) Truncate table userinfo;

ix) drop table userinfo;



4=> create table country(countryid int primary key auto_increment,countryname varchar(100));


create table state(stateid int primary key auto_increment,statename varchar(100),countryid int,foreign key(countryid) references state(countryid));


create table city(cityid int primary key auto_increment,cityname varchar(100),stateid int,FOREIGN KEY(stateid) references state(stateid));

5=>create table login_info(user_id int primary key,passw varchar(10) not null );


6=> alter table login_info ADD HINT_QUES varchar(30);

alter table login_info drop column HINT_QUES;

alter table login_info modify passw varchar(15);



7=> create table EMPLOYEES(Employee_id int primary key,Employee_Name varchar(20) NULL);



CREATE TABLE ORDERS(Product_id int primary key,product varchar(20) NULL, Employee_id int,FOREIGN KEY(Employee_id) references EMPLOYEES(Employee_id);


8=> Insert into EMPLOYEES values(1001,"Karan"),(1002,"Shikhar"),(1003,"Rajan"),(1004,"Priya");

Insert into ORDERS VALUES(1,"Table",1001),(2,"chair",1002),(3,"Printer",1003),(4,"Projector",NULL);


9=> SELECT employees.Employee_Name,ORDERS.Product from employees,ORDERS where employees.Employee_id = ORDERS.Employee_id;


select employees.Employee_Name , ORDERS.Product from employees left join ORDERS on employees.Employee_id = ORDERS.Employee_id;


select employees.Employee_Name , ORDERS.Product from employees RIGHT join ORDERS on employees.Employee_id = ORDERS.Employee_id;




                                      DATABASE SESSION                DATE :-17/06/2026


View:- View is a logical table, which is created from another table. If you perform insert,update or delete in view then main table will also be affected.
 
Syntax:= create view <viewname> as select <column1>,<column2> from <table name>;

     create table staff(

                      staffid int primary key,
                         staffname varchar(50),department varchar(50),salary bigint);



    create view stf as select staffid, staffname, department from staff;


Drop the view := drop VIEW stf;





Stored procedure:= Stored procedure is a pre-compiled query, which is developed in database in form of procedure and it is consumed in backend.


Date:18/06/2026



GROUP BY — It is used to arrange rows having same value into groups.it is commonly used with aggregate function.


create table spiemp(
empid int primary key,
empname varchar(50),department varchar(50),salary bigint);
 

insert into spiemp values(1,"Amit","HR",30000),(2,"Ravi","IT",50000),(3,"Priya","HR",350000),(4,"Neha","IT",45000),(5,"Mohan","Sales",40000),(6,"Karan","IT",55000);



EX1:- Count Employees in each department.
Ex2:- Find Total Salary Department-wise.

select department,count(*)"NO. Of Employees" from spiemp group by department;

select department,count(*)"No. of  Employee" from employee group by department;


select department,sum(salary)"Total salary" from spiemp group by department;







Table Name : customer


cid | int |Primary Key| A_I |
cname| varchar(50)|         |not null|
address| varchar(500)
contact_no | varchar(15)
































<!-- ========================================================= -->
<!--                 PREMIUM DEVELOPER PROFILE                 -->
<!-- ========================================================= -->

<div align="center">

<img
  src="https://capsule-render.vercel.app/api?type=waving&color=0:0F172A,40:1E3A8A,70:2563EB,100:0EA5E9&height=250&section=header&text=Arpit%20Rai&fontSize=72&fontColor=FFFFFF&fontAlignY=35&animation=twinkling&stroke=60A5FA&strokeWidth=1"
  width="100%"
  alt="Arpit Rai Header"
/>

<br>

<img
  src="https://readme-typing-svg.demolab.com?font=Poppins&weight=600&size=24&pause=1000&color=38BDF8&center=true&vCenter=true&width=850&lines=Hi+there!+I'm+Arpit+Rai+%F0%9F%91%8B;Computer+Science+Engineering+Student+%F0%9F%92%BB;Frontend+Developer+%7C+Tech+Enthusiast;Building+Real-World+Projects+%F0%9F%9A%80;Turning+Ideas+Into+Digital+Experiences+%E2%9C%A8"
  alt="Typing Animation"
/>

<br><br>

<img
  src="https://komarev.com/ghpvc/?username=arpitrai38&label=PROFILE%20VIEWS&style=for-the-badge&color=2563EB&labelColor=0F172A"
  alt="Profile Views"
/>

<img
  src="https://img.shields.io/github/followers/arpitrai38?label=FOLLOWERS&style=for-the-badge&color=2563EB&labelColor=0F172A&logo=github"
  alt="GitHub Followers"
/>

</div>

---

<!-- ========================================================= -->
<!--                       INTRODUCTION                         -->
<!-- ========================================================= -->

<div align="center">

## 👨‍💻 Welcome to My Digital Space

### `Developer • Learner • Builder`

<p>
I love transforming ideas into clean, useful and engaging
digital experiences.
</p>

</div>

<br>

<!-- ========================================================= -->
<!--                         PROFILE                            -->
<!-- ========================================================= -->

<table>
<tr>

<td width="42%" align="center" valign="middle">

<img
  src="arpit-rai-ascii-profile.png"
  alt="Arpit Rai ASCII Profile"
  width="100%"
/>

</td>

<td width="58%" valign="top">

## ✨ About Me

I'm **Arpit Rai**, a Computer Science Engineering student at  
**Institute of Technology and Management (ITM), GIDA, Gorakhpur**.

I'm passionate about **Web Development, Programming,
Problem Solving and building real-world applications**.

### 🎯 Currently Focused On

- 🌐 Modern Web Development
- ⚛️ React & Frontend Development
- 🧠 Data Structures & Algorithms
- 💻 C++ Programming
- 🚀 Full Stack Development
- 🎨 UI/UX and better user experiences
- 🔧 Building practical projects

### 💭 My Development Philosophy

```text
Learn → Build → Debug → Improve → Ship → Repeat
```
</td> </tr> </table>
<!-- ========================================================= --> <!-- DEVELOPER JOURNEY --> <!-- ========================================================= --> <div align="center">
🌱 My Developer Journey
</div> <table> <tr> <td width="33%" align="center" valign="top">
💡 Learn

Understanding technologies,
concepts and fundamentals.

📚

Curiosity drives growth

</td> <td width="33%" align="center" valign="top">
🛠️ Build

Turning ideas into
working applications.

💻

Ideas become products

</td> <td width="33%" align="center" valign="top">
🚀 Improve

Making projects cleaner,
faster and better.

⚡

Never stop improving

</td> </tr> </table>
<!-- ========================================================= --> <!-- CURRENT FOCUS --> <!-- ========================================================= --> <div align="center">
🔭 Currently Exploring
<br>

<img src="https://readme-typing-svg.demolab.com?font=Poppins&weight=500&size=18&pause=900&color=38BDF8&center=true&vCenter=true&width=700&lines=React.js+%E2%9A%9B%EF%B8%8F;Modern+Frontend+Development+%F0%9F%8C%90;Data+Structures+%26+Algorithms+%F0%9F%A7%A0;Full+Stack+Development+%F0%9F%9A%80;Building+Real-World+Projects+%F0%9F%92%BB" alt="Currently Exploring" />

</div>
<!-- ========================================================= --> <!-- FEATURED PROJECTS --> <!-- ========================================================= --> <div align="center">
🚀 Featured Projects
</div> <table> <tr> <td width="50%" valign="top">
🌍 WanderWise
Bharat Bharaman

A smart travel planning platform designed to help users
explore destinations and plan trips efficiently.

Highlights

🗺️ Travel Planning
💰 Budget-oriented trips
🧳 Destination Exploration
🎨 User-friendly Interface
🚀 Smart Travel Experience

Tech

HTML CSS JavaScript React Node.js

</td> <td width="50%" valign="top">
🎓 Grievance Redressal System

A web-based platform for managing student grievances
and tracking their resolution.

Highlights

📝 Complaint Submission
📊 Complaint Tracking
👨‍💼 Admin Management
🔄 Status Management
💬 Discussion Forum

Tech

React Node.js Express MongoDB

</td> </tr> <tr> <td width="50%" valign="top">
📚 ExamPrep

An examination preparation platform with authentication,
dashboards and question management.

Features

🔐 Authentication
📊 Student Dashboard
📝 Question Bank
📖 Subject Management
👨‍🎓 Examinee Management
🎯 Exam Preparation

Tech

React Node.js Express MongoDB

</td> <td width="50%" valign="top">
✈️ Sarthi
Travel Planner

A travel assistance platform designed to help tourists
plan trips according to their destination and budget.

Features

🗺️ Trip Planning
💰 Budget Planning
🌍 Destination Assistance
🧳 Travel Information

Tech

HTML CSS JavaaScript React

</td> </tr> <tr> <td width="50%" valign="top">
🛒 Zomato-Style Food Platform

A food discovery and ordering interface inspired by
modern food delivery platforms.

Focus

🍔 Restaurant UI
🔍 Search Experience
🏪 Restaurant Cards
📱 Responsive Design

Tech

HTML CSS JavaScript

</td> <td width="50%" valign="top">
🌦️ Weather Application

A weather application that provides weather information
through a clean and simple interface.

Focus

🌤️ Weather Information
🔎 Location Search
📱 Responsive UI
⚡ API Integration

Tech

HTML CSS JavaScript API

</td> </tr> <tr> <td width="50%" valign="top">
💧 Water Reminder

A simple productivity and wellness reminder application
designed to help users remember regular water intake.

Focus

⏰ Reminders
💧 Water Tracking
🎨 Simple UI
📱 Responsive Design

Tech

HTML CSS JavaScript

</td> <td width="50%" valign="top">
🏨 Hotel Management System

A desktop-based hotel management application built
for managing hotel-related operations.

Features

🏨 Room Management
👤 Customer Management
📋 Booking Management
🗄️ Database Integration

Tech

Python Tkinter MySQL

</td> </tr> <tr> <td width="50%" valign="top">
🧠 Amarsadhana

A supportive web platform focused on creating a
positive and engaging digital experience.

Focus

🎨 User Experience
🌐 Web Development
💡 Interactive Content
📱 Responsive Design

Tech

HTML CSS JavaScript

</td> <td width="50%" valign="top">
💻 iCoder

A programmer-focused blog and content platform with
modern Bootstrap-based UI.

Features

📝 Blog Interface
🧭 Navigation
🖼️ Carousel
📱 Responsive Layout
🔐 Login / Signup UI

Tech

HTML CSS Bootstrap JavaScript

</td> </tr> </table>
<!-- ========================================================= --> <!-- PROJECT MINDSET --> <!-- ========================================================= --> <div align="center">
🧩 How I Build Projects
</div>
              💡 IDEA
                 │
                 ▼
          🔎 RESEARCH
                 │
                 ▼
           🎨 DESIGN
                 │
                 ▼
            💻 CODE
                 │
                 ▼
           🐛 DEBUG
                 │
                 ▼
           🧪 TEST
                 │
                 ▼
          🚀 DEPLOY
                 │
                 ▼
          📈 IMPROVE
<!-- ========================================================= --> <!-- SKILLS --> <!-- ========================================================= --> <div align="center">
🛠️ Skills & Technologies
<br>
💻 Programming Languages

<img src="https://skillicons.dev/icons?i=cpp,js,python,html,css&theme=light" alt="Programming Languages" />

<br><br>

🎨 Frontend Development

<img src="https://skillicons.dev/icons?i=react,bootstrap,tailwind,vite&theme=light" alt="Frontend Skills" />

<br><br>

⚙️ Backend Development

<img src="https://skillicons.dev/icons?i=nodejs,express&theme=light" alt="Backend Skills" />

<br><br>

🗄️ Databases

<img src="https://skillicons.dev/icons?i=mongodb,mysql&theme=light" alt="Database Skills" />

<br><br>

🔧 Development Tools

<img src="https://skillicons.dev/icons?i=git,github,vscode,postman,figma&theme=light" alt="Development Tools" />

</div>
<!-- ========================================================= --> <!-- SKILL MATRIX --> <!-- ========================================================= --> <div align="center">
📌 Skill Matrix
</div> <table> <tr> <td width="50%" valign="top">
Frontend
HTML / CSS       ████████████████████ 95%
JavaScript       ██████████████████░░ 90%
React.js         ████████████████░░░░ 85%
Bootstrap        ██████████████████░░ 90%
Tailwind CSS     ███████████████░░░░░ 80%
</td> <td width="50%" valign="top">
Programming & Backend
C++              ████████████████░░░░ 85%
Node.js          ██████████████░░░░░░ 75%
Express.js       ██████████████░░░░░░ 75%
MongoDB          ██████████████░░░░░░ 75%
MySQL            ███████████████░░░░░ 80%
</td> </tr> </table>
<!-- ========================================================= --> <!-- DEVELOPMENT TOOLS --> <!-- ========================================================= --> <div align="center">
🔧 Tools I Use
<table> <tr> <td align="center"> 💻<br> <b>VS Code</b> </td> <td align="center"> 🐙<br> <b>GitHub</b> </td> <td align="center"> 🌿<br> <b>Git</b> </td> <td align="center"> 🚀<br> <b>Postman</b> </td> <td align="center"> 🎨<br> <b>Figma</b> </td> </tr> </table> </div>
<!-- ========================================================= --> <!-- GITHUB ANALYTICS --> <!-- ========================================================= --> <div align="center">
📊 GitHub Analytics
<br>

<img height="180" src="https://github-readme-stats.vercel.app/api?username=arpitrai38&show_icons=true&include_all_commits=true&count_private=true&hide_border=true&theme=tokyonight&bg_color=0F172A&title_color=38BDF8&icon_color=60A5FA&text_color=E2E8F0" alt="Arpit Rai GitHub Stats" />

<img height="180" src="https://github-readme-stats.vercel.app/api/top-langs/?username=arpitrai38&layout=compact&langs_count=8&hide_border=true&theme=tokyonight&bg_color=0F172A&title_color=38BDF8&text_color=E2E8F0" alt="Arpit Rai Top Languages" />

<br><br>

<img src="https://streak-stats.demolab.com?user=arpitrai38&theme=tokyonight&hide_border=true&background=0F172A&ring=38BDF8&fire=60A5FA&currStreakLabel=38BDF8&sideLabels=E2E8F0&dates=94A3B8" alt="Arpit Rai GitHub Streak" />

</div>
<!-- ========================================================= --> <!-- CONTRIBUTION GRAPH --> <!-- ========================================================= --> <div align="center">
📈 Contribution Activity
<br>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=arpitrai38&bg_color=0F172A&color=E2E8F0&line=38BDF8&point=FFFFFF&area=true&hide_border=true" width="95%" alt="GitHub Contribution Graph" />

</div>
<!-- ========================================================= --> <!-- TROPHIES --> <!-- ========================================================= --> <div align="center">

## 🏆 GitHub Achievements

<br>

<img
  src="https://github-profile-trophy.vercel.app/?username=arpitrai38&theme=algolia&no-frame=true&no-bg=true&margin-w=10&column=6"
  alt="GitHub Trophies"
/>

</div>
<!-- ========================================================= --> <!-- CONNECT --> <!-- ========================================================= --> <div align="center">
🌐 Let's Connect
<p> I'm always open to learning, collaborating and building interesting things. </p> <br> <a href="https://github.com/arpitrai38">

<img src="https://img.shields.io/badge/GitHub-0F172A?style=for-the-badge&logo=github&logoColor=FFFFFF" alt="GitHub" />

</a>

  

<a href="https://www.linkedin.com/in/arpit-rai-002951292">

<img src="https://img.shields.io/badge/LinkedIn-2563EB?style=for-the-badge&logo=linkedin&logoColor=FFFFFF" alt="LinkedIn" />

</a>

  

<a href="mailto:sadhanamarendra12@gmail.com">

<img src="https://img.shields.io/badge/Email-0EA5E9?style=for-the-badge&logo=gmail&logoColor=FFFFFF" alt="Email" />

</a> </div>
<!-- ========================================================= --> <!-- FOOTER --> <!-- ========================================================= --> <div align="center">
💙 Thanks for visiting my profile!
<br>

<img src="https://readme-typing-svg.demolab.com?font=Poppins&weight=500&size=16&pause=1200&color=64748B&center=true&vCenter=true&width=700&lines=Keep+Learning+%7C+Keep+Building+%7C+Keep+Growing+%F0%9F%9A%80" alt="Footer Animation" />

<br><br>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0EA5E9,40:2563EB,70:1E3A8A,100:0F172A&height=130&section=footer" width="100%" alt="Footer" />

</div> ```




























 
