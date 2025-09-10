# Level 26 → 27 🔐

---

## 🎯 Goal  

Retrieve the password for Bandit27 by interacting with the **setuid binary** provided in Bandit26.  
This level teaches how setuid binaries can be exploited to perform actions as another user.  

---

## 🛠 Commands Used  

- `ls` – List files in a directory  
- `file` – Determine file type and permissions  
- `./<binary>` – Execute the setuid binary with arguments  
- `whoami` – Check effective user identity  
- `cat` – Read the password file  

---

## 🚀 How to Solve  

1. **Log in as bandit26:** 
    ```bash
    ssh bandit26@localhost -p 2220
    ```

2. **List the files in your home directory:**  
    ```bash
    ls
    ```
  - You should see a file named `bandit27-do`.  

3. **Check what kind of file it is:**  
    ```bash
    file bandit27-do
    ```
  - It will show that it is a **setuid binary**.  

4. **Execute the binary with `whoami` to see its effective user:** 
    ```bash
    ./bandit27-do whoami
    ```
  - The output will show `bandit27`, meaning the binary runs with Bandit27’s privileges.  

5. **Use the binary to read Bandit27’s password:**  
    ```bash
    ./bandit27-do cat /etc/bandit_pass/bandit27
    ```
  - The password for Bandit27 will be displayed.  

---

## 💡 Bonus Tips  

- Setuid binaries allow you to **perform actions as another user**, which is the core trick in this level.  
- You can combine `./bandit27-do` with almost any command, like `ls` or `cat`, to perform actions **as Bandit27**.  
- Always check file type and permissions first (`file` and `ls -l`) to understand the binary’s behavior.  

---

## 🧠 Why This Level Matters  

- Demonstrates how **setuid binaries can be exploited** to gain access to another user’s files.  
- Reinforces understanding of **file permissions and effective user identity**.  
- Provides a controlled environment to practice **privilege escalation techniques**.  
