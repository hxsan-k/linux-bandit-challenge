# Level 22 → 23 ⏰  

---

## 🎯 Goal  

Another program is running automatically at regular intervals using **cron**.  
This time, the cronjob points to a script that should be simple to read.  
Your task: understand what the script does and use it to get the next password.  

---

## 🛠 Commands Used  

- `ls /etc/cron.d/` – list cron job configs  
- `cat` – view cronjob and script contents  
- `echo` – see what certain commands produce  
- `md5sum` – generates a hash (used inside the script)  

---

## 🚀 How to Solve  

### 1. List the cron jobs with:
   ```bash
   ls /etc/cron.d/
   ```
### 2. Inspect the cronjob for this level using:
   ```bash
   cat /etc/cron.d/cronjob_bandit23
   ```
### 3. Follow the script path with:
   ```bash
   cat /usr/bin/cronjob_bandit23.sh
   ``` 
   - Explanation of the script:  
     - Gets the username with `whoami`  
     - Creates a string `"I am user <username>"`  
     - Hashes it with `md5sum`  
     - Uses that hash as the filename in `/tmp`  
     - Copies the user’s password file (`/etc/bandit_pass/<username>`) into that hash-named file
       
### 4. Reproduce what the script does manually:  
   ```bash
   echo I am user bandit23 | md5sum | cut -d ' ' -f 1
   ```
   This gives you the hash (filename)
   
### 5. Finally, read the password:
   ```bash
   cat /tmp/<that_hash>
   ```

---

## 💡 Bonus Tips  

- Scripts often use variables and simple shell tools. Don’t overthink it, just trace each step.  
- If you’re unsure what part of a script does, try running that single command in your terminal.  

---

## 🧠 Why This Level Matters  

This level teaches you to **read and reason through shell scripts** written by others.  
Instead of just running commands blindly, you’re learning to break a script into steps: input → process → output.

That skill is gold when debugging, auditing, or exploiting automation on real systems.  
