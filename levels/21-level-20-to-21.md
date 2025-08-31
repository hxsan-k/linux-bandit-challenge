# Level 20 → 21 🔐

---

## 🎯 Goal  

Retrieve the next level’s credentials by interacting with a setuid binary in the home directory that connects to a server on localhost.  
The binary reads a line of text from the connection, checks if it matches the current level’s password (bandit20), and if correct, sends back the next password (bandit21).

---

## 🛠 Commands Used  

- `nc` (netcat) – Listen for and send data over TCP connections  
- `cat` – Display the current password  

---

## 🚀 How to Solve  

1. Open a terminal and start a netcat listener on a port above 1024 (e.g., 4444) to act as the server:
```bash
   nc -lvp 4444 
```
2. In the listener terminal, when a connection comes in, manually type (or paste) the bandit20 password:
```bash
   cat /etc/bandit_pass/bandit20
```
3. In a second terminal, run the setuid binary and point it to the port your listener is using:
```bash
  ./suconnect 4444
```
4. Once the password is verified, the binary will send the bandit21 password back through the same connection. This will appear in your listener terminal.  

5. Copy the bandit21 password from the listener terminal; this is the credential for the next level  

6. Close the netcat listener once you have the password 
---

## 🔢 Quick Explanation: setuid binary & client/server  

- The `suconnect` binary is the client: it initiates a connection to the listener on localhost and expects to receive the current password.  
- Your netcat listener acts as the server: it waits for connections and supplies the requested password to the client.  
- Once the client verifies the password is correct, it sends back the next password, which you capture in the netcat terminal.  

---

## 💡 Bonus Tips  

- Always choose a port number above 1024 for the listener; lower ports require root privileges and will give “Permission denied.”  
- Piping the current password into netcat automates sending it as soon as a connection is made, avoiding manual typing delays.  
- Using the two-terminal approach helps you clearly see what the client sends and what the server receives.  

---

## 🧠 Why This Level Matters  

This level teaches a practical understanding of client/server communication and TCP connections on localhost.  

Think of it like this: the client (`suconnect`) is a VIP auditor visiting your server (nc). The auditor needs some information to verify themselves (bandit20 password), and once satisfied, they hand back a reward (bandit21 password).  

You learn to:  

- Set up a listener to act as a server  
- Understand the flow of information between client and server  
- Handle a challenge where the “client” holds authority, not the server, which is counterintuitive but common in real network protocols  

It’s a simple but powerful exercise in network reasoning and working with setuid binaries.
