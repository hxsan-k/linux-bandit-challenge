# Level 14 → 15 🔐

---

## 🎯 Goal

Submit the password for the current level (Bandit14) to port `30000` on `localhost`, which will return the password for the next level

---

## 🛠 Commands Used

- `nc` (Netcat) – A networking tool for reading/writing data across network connections.  
  Useful for making raw TCP/UDP connections.

---

## 🚀 How to Solve

1. **Login with the bandit14 username**:

```bash
ssh bandit14@bandit.labs.overthewire.org -p 2220
```

2. To submit the password to port 30000 on localhost (like the task requires), run:

```bash
nc localhost 30000
```

This command sends the password directly over a TCP connection to port 30000, and the server responds with the password for the next level.

3. A blinking cursor will appear on the next line.

Here, enter the password of the previous level (same one you used to login with the bandit14 username):

```bash
[enter the password]
```

4. If entered correctly, you will see the following message:

```bash
[password you entered for the previous level]
Correct!
[password for the next level]
```

---

## 💡 Bonus Tips

If the connection closes instantly or nothing returns, double check the port or syntax.

Netcat is often called the “Swiss army knife” of networking – it can open connections, transfer files, scan ports, and more.

---

## 🧠 Why This Level Matters

This level introduces the concept of interacting with network services using TCP sockets. 

Being able to send and receive data over specific ports is fundamental in DevOps, security testing, and server diagnostics. Tools like nc let you explore what’s going on behind the scenes without fancy clients – just raw input and output.
