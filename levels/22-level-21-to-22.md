# Level 21 → 22 ⏰  

---

## 🎯 Goal  

A program is running automatically at regular intervals using **cron** (the time-based job scheduler).  
Your task: figure out what it’s doing and grab the password for the next level.  

---

## 🛠 Commands Used  

- `ls /etc/cron.d/` – list cron job configs  
- `cat` – view contents of a cron job file  
- `grep` – search inside files (optional but handy)  
- `cat` – read the file where the password gets stored  

---

## 🚀 How to Solve  

1. Check the cron jobs directory with
   ```bash
   ls /etc/cron.d/
   ```
2. Inspect the relevant cronjob file with
   ```bash
   cat /etc/cron.d/cronjob_bandit22
   ```
3. Follow the script path to see what it does using
   ```bash
   cat /usr/bin/cronjob_bandit22.sh
   ```
   The script takes the current username, hashes it, and writes the password to a temporary file based on that hash.
   
5. Finally, read the file where the password is stored with
   ```bash
   cat /tmp/<filename_here>
   ```

---

## 💡 Bonus Tips  

- Cron jobs are like “robots” running commands on a schedule. Reading their configs can reveal exactly what they’re automating.  
- Always trace the chain: cronjob → script → where it writes output.  

---

## 🧠 Why This Level Matters  

This level introduces you to **cron jobs**, which are one of the most common ways that Linux handles automation.  
It shows how scheduled scripts can move data around behind the scenes… and how reading those configs gives you insight (or access 👀).  
