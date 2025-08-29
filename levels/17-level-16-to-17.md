# Level 16 → 17 🔐

---

## 🎯 Goal  

Retrieve the next level’s credentials by submitting the current password to a server running on localhost.  
The server is listening on one port in the range 31000–32000.  
Some ports echo data back, others expect SSL/TLS. Only **one** will actually hand over the next credentials.  

---

## 🛠 Commands Used  

- `nmap` – Scan ports and check which ones are open  
- `openssl s_client` – Connect to an SSL/TLS server  
- `nc` (netcat) – Send data over a non-encrypted connection  
- `grep` – Filter and search output  

---

## 🚀 How to Solve  

1. Scan for open ports in the range 31000–32000:  
```bash
nmap -p 31000-32000 localhost
```

Note down open the ports for the next step.

2. Test each open port with netcat:  
```bash
nc localhost <port>
```

Type in the current password each time and press enter.  
If the port just echoes the same thing back, ignore it.  
If it behaves strangely (connection hangs or replies with something else, that's your clue it may be SSL/TLS)

3. Check remaining ports for SSL/TLS servers using openssl:  
```bash
openssl s_client -connect localhost:<port>
```

Paste in the current password when connected.  
One of these will finally give you something useful — the private SSH key for Bandit17.  

4. Save the private key:  
```bash
nano bandit17_key
```

6. Fix the key permissions (otherwise SSH will refuse it):  
```bash
chmod 400 bandit17_key
```

8. Log in to Bandit17 (the next level) using the key:  
```bash
ssh -i [file path to bandit17_key] bandit17@bandit.labs.overthewire.org -p 2220
```

---

## 🔢 Quick Explanation: openssl s_client  

- `s_client` is like `nc`, but it talks over SSL/TLS instead of plain text.  
- It’s useful for debugging secure connections or testing if a port expects encryption.  
- If you try `nc` on a port that needs SSL, you’ll just see garbage or get disconnected.  

---

## 💡 Bonus Tips  

- When you’re not sure if a service needs SSL, try both `nc` and `openssl s_client`.  
- Port scanning with nmap saves loads of time compared to trying every port manually.  
- Always remember to lock down private keys with `chmod 400`.
- `chmod` only works with Linux. If your key file is saved on a Windows drive, you will need to copy the key into your Linux home directory using the `cp` command first.

---

## 🧠 Why This Level Matters  

This level introduces a practical mix of network scanning, encryption, and authentication.  

You learn how to:  

- Identify listening ports  
- Differentiate between plain-text and SSL/TLS connections  
- Handle real-world tools (`nmap`, `nc`, `openssl`) used by sysadmins and security engineers daily  

And most importantly, you get your hands on another private key — proving once again that half the battle in Linux is just knowing which tool to use.  
