## Ex. No: 5
# Creating Triggers using PL/SQL

## AIM: 
To create a Trigger using PL/SQL.

## Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

## Program:
### Create worker table
```
CREATE TABLE worker
(
empid NUMBER,
empname VARCHAR2(10)
dept VARCHAR2(10),
salary NUMBER
);
```

### Create vj_log table
```
CREATE TABLE vj_log
(
log_id NUMBER GENERATED ALWAYS AS IDENTITY,
empid NUMBER,
empname VARCHAR2(10),
old_salary NUMBER,
new_salary NUMBER,
update_date DATE
);
```
### PLSQL Trigger code
```
CREATE OR REPLACE TRIGGER logging_insurence_update
BEFORE UPDATE ON worker
FOR EACH ROW
BEGIN
IF :OLD.salary != :NEW.salary THEN
INSERT INTO vj_log (empid, empname, old_salary, new_salary, update_date)
VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
END IF;
END;
/
```

### Inserting data into workertable
```
insert into worker values(1,'diya','sales',10000);
insert into worker values(2,'vidya','manager',20000);
insert into worker values(3,'nithya','hr',30000);

```
### update the salary of the worker
```
UPDATE worker
set salary = 12000
where empid=3;
```
### Display the worker table
```
select * from worker;
```
### Display the vj_log table
```
select * from vj_log;
```
## Output:
### create table for worker:
![image](https://github.com/MSowmya28/Ex-5-Creating-Triggers-using-PL-SQL/assets/94154791/3869777c-9e37-4236-a7f6-37d033994a6e)
### create table for vj_log:
![image](https://github.com/MSowmya28/Ex-5-Creating-Triggers-using-PL-SQL/assets/94154791/bf60786f-b64a-4a2f-b83b-cfee5790900a)
### insert the data into the worker table
![image](https://github.com/MSowmya28/Ex-5-Creating-Triggers-using-PL-SQL/assets/94154791/089c6208-8e4f-479c-8455-c35a43c4f904)


### create a trigger named logging_insurance_update
![image](https://github.com/MSowmya28/Ex-5-Creating-Triggers-using-PL-SQL/assets/94154791/e57bf93e-2f5d-4f15-9a3b-2f36bee7b06f)


### Display the worker table
![image](https://github.com/MSowmya28/Ex-5-Creating-Triggers-using-PL-SQL/assets/94154791/a9b7c4eb-e19f-4c07-a1c5-8a803bea3a7f)


### update the worker table
![image](https://github.com/MSowmya28/Ex-5-Creating-Triggers-using-PL-SQL/assets/94154791/7c852acc-d743-4a23-9317-b904bc550253)


### display the vj_log:
![image](https://github.com/MSowmya28/Ex-5-Creating-Triggers-using-PL-SQL/assets/94154791/3138ced1-b4ac-4d5e-839b-e7dc1671bbf3)

## Result:
The program has been implemented successfully.
