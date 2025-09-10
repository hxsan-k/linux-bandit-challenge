# Level 24 → 25 🔐

---

## 🎯 Goal  

Retrieve the next level’s credentials by interacting with a daemon listening on **port 30002**.  
The daemon requires the **current password (bandit24)** and a **secret 4-digit PIN**, which is unknown.  
The only way to get the correct PIN is by **brute-forcing all 10,000 combinations**, which can be done efficiently by **creating a list of all possible PINs and feeding it to the daemon**.  

---

## 🛠 Commands Used  

- `nc` (netcat) – Send data to a TCP service on localhost  
- `echo` – Generate password + PIN combinations  
- `cat` – Send a file of combinations to the daemon  

---

## 🚀 How to Solve  

1. Create a directory for your scripts (optional):
    ```bash
    mkdir /tmp/scriptdir
    ```
    ```bash
    cd /tmp/scriptdir
    ```
2. Write a script to generate all password+PIN combinations:
    ```bash
    #!/bin/bash
    
    for i in {0000..9999}  
    do
         echo "<Password for Bandit24> $i" >> list.txt
    done
    ```
    Replace `<Password for Bandit24>` with your **current Bandit24 password**. This script will create a file `list.txt` containing all 10,000 possible combinations.

3. Make the script executable and run it:  
    ```bash
    chmod +x generate_list.sh
    ```
    ```bash
    ./generate_list.sh
    ```
4. Send all combinations to the daemon on port 30002:  
    ```bash
    cat list.txt | nc localhost 30002
    ``` 
   The daemon will process each line sequentially. Only the correct combination will return a message like **“Correct”** and reveal the **Bandit25 password**.

5. Watch the output and grab the password for Bandit25!

---

## 🔢 Step-by-Step Explanation

1. **`for i in {0000..9999}`**  
   - Loops through every 4-digit combination from `0000` to `9999`.  

2. **`echo "bandit24_password $i" >> list.txt`**  
   - Writes the current password + PIN combination to `list.txt`.  
   - `>>` appends each new line so all 10,000 combinations are saved. ( `>` would replace each line with the most recent one) 

3. **`cat list.txt | nc localhost 30002`**  
   - Sends every line from `list.txt` to the daemon in one go.  
   - The daemon checks each combination and prints **bandit25’s password** when it finds the correct PIN.  

---

## 🧠 Why This Level Matters  

This level teaches **automation and scripting** to interact with network services.  

- You learn to generate input files for brute-force testing.  
- You see how batching multiple inputs into a single `nc` session improves efficiency.  
- It’s a controlled demonstration of how automated scripts can replace tedious manual tasks.  
