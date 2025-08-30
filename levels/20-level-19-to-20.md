# Level 19 → Level 20 🔐

---

## 🎯 Goal  
You’ll find a special program (setuid binary) in your home directory. Run it without arguments to see what it does. Use it to grab the password for the next level, which is stored in the usual place: /etc/bandit_pass/bandit20.  

---

## 🛠️ Commands Used

- `ssh` – Log in to the server
- `ls` – List files in a directory
- `cat` – View the contents of a file
- `./<binary>` – Run the binary in the current directory

---

## 🚀 Steps  
1. Log into bandit19:  
   ```bash
   ssh bandit19@bandit.labs.overthewire.org -p 2220
   ```
   (Password is from previous level)  

2. List the files in your home directory:  
   ```bash
   ls
   ```
   You should see something like:  
   `bandit20-do`  

3. Run the program without arguments to see what it does:  
   ```bash
   ./bandit20-do
   ```
   Expected output:  
   `Run a command as another user. Example: ./bandit20-do id ` 

4. Use it to read the password file for bandit20:  
   ```bash
   ./bandit20-do cat /etc/bandit_pass/bandit20
   ``` 
   Output:  
   `<this will show the password for bandit20>`  

✅ You now have the password for bandit20.  

---

## 📘 Quick Explanation – What’s going on with setuid?  

- Normally, when you run a program, it runs with *your* permissions.  
- A setuid binary is different: it always runs with the permissions of the file’s owner (in this case, bandit20).  
- That’s why you can read the /etc/bandit_pass/bandit20 file, even though you wouldn’t normally have access.  
- Being in the home directory matters because the binary is only available there, and running it elsewhere without the correct path (./) won’t work since it’s not in your $PATH.  
