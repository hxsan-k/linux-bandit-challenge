# Level 15 → 16 🔒  

---

## 🎯 Goal  

The password for the next level can be obtained by sending the current level’s password to `localhost` on port `30001` using SSL/TLS encryption. Once sent, the server will respond with the password for the next level.  

---

## 🛠 Commands Used  

- `ssh` – Connects to the remote Bandit server  
- `openssl s_client` – Connects to a remote host over SSL/TLS  
- `cat` – Reads and outputs file contents  

---

## 🚀 How to Solve  

1. Log in to Bandit level 15:

```bash
ssh bandit15@bandit.labs.overthewire.org -p 2220  
```

2. Ensure you have the password for Bandit User 15 (which you just logged in with).

3. Connect to the SSL/TLS service running on port 30001.

- According to the man page for `openssl s_client`, the syntax is the following:
  - `openssl s_client [-connect host:port]`

- This gives us:
```bash
openssl s_client -connect localhost:30001  
```

4. When prompted, paste the current level’s password and press Enter.  
   The server will then send a `Correct!` message along with the password for the next level.
   
---

## ⚡ One-Liner Method  

If you want to send the password directly without manually typing it in:  
```bash
cat /etc/bandit_pass/bandit15 | openssl s_client -connect localhost:30001 -quiet  
```

Here’s what happens:  
- `cat` outputs the current password.  
- The pipe (`|`) sends it as input to `openssl s_client`.  
- The `-quiet` flag hides extra connection messages that are normally shown in the output.  

---

## 💡 Bonus Tips  

- If you see DONE, RENEGOTIATING, or KEYUPDATE, it means the connection closed or you sent extra input. Just try again and send only the password.  
- The `openssl s_client` command is useful beyond CTFs — it’s handy for testing SSL/TLS connections in real-world systems.  

---

## 🧠 Why This Level Matters  

This challenge teaches you how to interact with encrypted network services directly from the terminal. It’s an introduction to tools like `openssl``, which are essential for testing secure connections, debugging SSL issues, and even performing secure data transfers in admin and DevOps work.
