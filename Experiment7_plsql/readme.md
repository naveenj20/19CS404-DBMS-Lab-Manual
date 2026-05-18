# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## NAME - NAVEEN JAISANKER
## REG. NO. : 212224110039
## DATE - 18/05/2026

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Greater number is: 80

## PROGRAM

```sql
DECLARE
    a NUMBER := &a;
    b NUMBER := &b;
BEGIN
    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
    END IF;
END;
/
```

## OUTPUT
<img width="777" height="301" alt="image" src="https://github.com/user-attachments/assets/8350a069-d655-4c54-862b-fe96bd2b599c" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Sum of first 10 natural numbers is: 55

## PROGRAM

```sql
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := &n;
    i NUMBER := 1;
    sum_val NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        sum_val := sum_val + i;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Sum is: ' || sum_val);
END;
/
```

## OUTPUT
<img width="851" height="350" alt="image" src="https://github.com/user-attachments/assets/4ee938cf-c43b-4792-9a74-c3106b90b66f" />

---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

## PROGRAM

```sql
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := &n;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');

    IF n >= 1 THEN
        DBMS_OUTPUT.PUT(a || ' ');
    END IF;

    IF n >= 2 THEN
        DBMS_OUTPUT.PUT(b || ' ');
    END IF;

    i := 3;

    WHILE i <= n LOOP
        c := a + b;
        DBMS_OUTPUT.PUT(c || ' ');
        a := b;
        b := c;
        i := i + 1;
    END LOOP;

    DBMS_OUTPUT.NEW_LINE;
END;
/
```
## OUTPUT
<img width="808" height="330" alt="image" src="https://github.com/user-attachments/assets/e21d1466-a6ce-467b-a386-855ee8b94323" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

## PROGRAM

```sql
SET SERVEROUTPUT ON;

DECLARE
    n NUMBER := &n;
    rev NUMBER := 0;
    rem NUMBER;
BEGIN
    WHILE n > 0 LOOP
        rem := MOD(n, 10);
        rev := rev * 10 + rem;
        n := FLOOR(n / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed number is: ' || rev);
END;
/
```

## OUTPUT
<img width="950" height="372" alt="image" src="https://github.com/user-attachments/assets/ad097d4e-620c-4c68-83ad-48eee9facef8" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

## PROGRAM

```sql
SET SERVEROUTPUT ON;

DECLARE
    a NUMBER := &a;
    b NUMBER := &b;
    c NUMBER := &c;
    largest NUMBER;
BEGIN
    IF a > b AND a > c THEN
        largest := a;
    ELSIF b > c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('Largest number is: ' || largest);
END;
/
```

## OUTPUT
<img width="773" height="341" alt="image" src="https://github.com/user-attachments/assets/0d796cb1-1262-4cd1-b500-079f1c9c1ee1" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
