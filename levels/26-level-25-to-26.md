# Level 25 → 26 🔐

---

## 🎯 Goal  

Retrieve the Bandit26 key file from bandit25’s home directory.  
There’s no tricks here. This is just preparation for the next level, where things get a bit *strange*.

---

## 🛠 Commands Used  

- `ls` – List files in a directory  
- `cat` – Read the key file  

---

## 🚀 How to Solve  

1. Log in as bandit25:  
`ssh bandit25@localhost -p 2220`  

2. Check the home directory for the key:  
`ls`  

- You should see `bandit26.sshkey`.  

3. Display the contents of the key file:  
`cat bandit26.sshkey`  

- The terminal will show the key starting with `-----BEGIN RSA PRIVATE KEY-----` and ending with `-----END RSA PRIVATE KEY-----`.  

4. Copy **all of the contents** from the terminal and save it on your **local machine** in a file, for example `bandit26.sshkey`.  

5. Change the permissions on your local copy so it is secure and usable:  
`chmod 600 bandit26.sshkey`  

- Now the key file is ready to use for logging into Bandit26 in the next level.  
