# Level 0 🐣

---

## 🎯 Goal

Log into the Bandit game using SSH.

- **Host:** bandit.labs.overthewire.org  
- **Port:** 2220  
- **Username:** bandit0  
- **Password:** bandit0  

## 🛠 Commands Used

- `ssh` — Connect to a remote server securely.

---

## 🚀 How to Solve

Run this command from your terminal:

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

## 💡 Bonus Tips
- Use -p to specify a non-standard SSH port like 2220.
- Make sure your terminal supports SSH connections.
- On Windows? Using Ubuntu via WSL is highly recommended.
- To install WSL (if you haven’t already), run this in PowerShell:

```powershell
wsl --install
```

## 🤔 Why This Level Helps
Learning to connect to remote servers securely is a foundational skill for any cloud or sysadmin role.
