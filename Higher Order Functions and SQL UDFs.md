# Higher Order Functions and SQL UDFs
<b> Data Used </b> <br>
<img width="901" alt="image" src="https://github.com/user-attachments/assets/376ed226-2347-4b80-8c15-1fcb78eadbb8" />

## Higher Order Functions:
<b>These functions are used to work with Hierarchial data such as arrays and map type objects. </b><br>
In Spark SQL, when using higher-order functions like FILTER, you must provide a lambda variable — an identifier (like i) that represents each element of the array you're filtering. <br>
### 1. Filter Operation
Proper usage of the FILTER function:
<br>1. books is an array (maybe of structs with fields like title, author, quantity, etc.).
<br>2. i -> i.quantity >= 2 is a lambda expression saying: "For each element i in books, keep it only if i.quantity >= 2." <br>
<img width="893" alt="image" src="https://github.com/user-attachments/assets/abf9880c-9c04-4cce-b883-ca061e45c674" />
<br>
<br> To remove empty values in the above result: <br>
<img width="385" alt="image" src="https://github.com/user-attachments/assets/fd010dc1-c877-48c2-93a5-c8c2f3258fad" />
<br> <br>
### 2. Transforming Arrays
<img width="826" alt="image" src="https://github.com/user-attachments/assets/81638ccb-0b26-43e0-9d53-48abe5fc5af6" />
### 3. User Defined Functions (UDFs)
UDF are permanent objects that are persisted to the database and hence can be used between different spark sessions and notebook. <br>
<img width="380" alt="image" src="https://github.com/user-attachments/assets/2f905ce0-2da7-40c2-9e01-f0bdd902aca9" /> <br>
<img width="239" alt="image" src="https://github.com/user-attachments/assets/a837cd8f-13de-43f0-86bc-0dbb5ea7c185" /> <br>
<img width="556" alt="image" src="https://github.com/user-attachments/assets/a8d68a6a-09e5-460b-afd5-3850a34bb4aa" /> <br>
More complex UDF: <br>
<img width="487" alt="image" src="https://github.com/user-attachments/assets/b288e492-f6e1-4ac0-ad1e-2dc2148c40bf" /> <br>



