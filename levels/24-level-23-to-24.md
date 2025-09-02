# Level 23 → 24 🔐  

---

## 🎯 Goal  

A cron job runs automatically as user `bandit24`. The script deletes itself after running, so you’ll need to create your own script in the right place to make it reveal the password for the next level.  

This is your first real shell script challenge, but don't worry, it's not nearly as messy as you think it might be.

---

## 🛠 Commands Used  

- `cat` – View file contents  
- `touch` – Create text files (in this case a script file)
- `nano` – Edit files 
- `chmod` – Set permissions so scripts can be executed  
- `ls -hl` – Verify files exist and check permissions  

---

## 🚀 How to Solve  

1. Look at the cron configuration for `bandit24` in `/etc/cron.d`:  
   ```bash
   cat /etc/cron.d/cronjob_bandit24
   ```
   You’ll see it runs a script every minute as `bandit24`.  

2. Check what that script is doing:  
   ```bash
   cat /usr/bin/cronjob_bandit24.sh
   ```  
   You’ll notice it executes any file placed in `/var/spool/bandit24/foo`.
    
   Then, it deletes the script after running it.  

3. This means you can drop your own script into `/var/spool/bandit24/foo`, and it will run as `bandit24`. Since `bandit24` has access to `/etc/bandit_pass/bandit24`, you can make your script copy that password into a world-readable place (like `/tmp`).  

4. Write your script:
   ```bash  
   #!/bin/bash
   
   cat /etc/bandit_pass/bandit24 > /tmp/mysecret
   ```  
   Save this as `/var/spool/bandit24/foo/myscript.sh`.  

5. Make it executable **immediately after saving** (the script might be deleted before you chmod it due to the *other* script that will run yours):  
   ```bash
   chmod 755 /var/spool/bandit24/foo/myscript.sh
   ```

6. Wait a minute for the cron job to run. Then check the file you wrote to:  
   ```bash
   cat /tmp/mysecret
   ```
   That will contain the password for `bandit24`. 🎉  

---

## ⚡️ Important Note  

Because the cron job deletes your script after running it, you have to be fast:  
- Save the file  
- Run `chmod` immediately  
- Otherwise cron may delete it before it becomes executable  

---

## 🔄 Alternative Method  

Instead of writing the file and then rushing to chmod it, you can create it with the right permissions from the start:  

```bash
echo '#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/mysecret' > /var/spool/bandit24/foo/myscript.sh
chmod 755 /var/spool/bandit24/foo/myscript.sh
```
Here’s what’s happening step by step:

- `echo` → writes the script content into a file.
- `#!/bin/bash` → ensures the script runs with bash.
- `cat /etc/bandit_pass/bandit24 > /tmp/mysecret` → copies the password into /tmp/mysecret when executed.
- `> /var/spool/bandit24/foo/myscript.sh` → sends the echo output into the script file.
- `chmod 755` → ensures cron (and others) can read + execute the script.

---

## 💡 Bonus Tips  

- `755` (or `-rwxr-xr-x`) is the right permission because the system needs read + execute access to your script as it is a text file, not binary.  
- If you set it to `711` or `-rwx--x--x`, only you could read it, so cron wouldn’t work.  
- Always think in terms of: "who needs to read this, who needs to run this?"  

---

## 🧠 Why This Level Matters  

This is the first time you’re writing your own script to escalate access.  

It teaches you:  

- How cron jobs can run your code as another user  
- Why permissions (chmod) matter in automation  
- How to design a script to output sensitive data somewhere you can reach  
- That automation doesn’t care about your mistakes, it will just fail silently if permissions are wrong  

This level is like a mini “exploit sandbox”: you get to inject code into a trusted process. In the real world, that’s a massive deal. 🚀  
