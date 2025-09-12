# Level 25 → 26 🔐

---

## 🎯 Goal  

Here, you would use the **Bandit26 SSH key** from Bandit25 to log in and retrieve Bandit26’s password...
But key itself isn’t directly usable; the SSH session initially **closes immediately**, which is part of the puzzle. You need to manipulate the terminal to proceed.  

---

## 🛠 Commands Used  

- `ssh` – Log in using the SSH key  
- `ls` – List files and directories  
- `cat` – Read password files  
- `vi` – Break out of the restricted shell into a normal bash shell  

---

## 🚀 How to Solve  

### 1. Run the SSH command with the key:
```bash
ssh bandit26@localhost -i bandit26.sshkey
``` 
Initially, the connection closes immediately.
  
### 2. Make the terminal window on your machine ***small vertically*** so the `--More--` prompt appears when connecting.

### 3. Run the *same SSH command again*, now with the terminal small enough to trigger `--More--`.

When `--More--` appears, press **`v`** to open the VI shell.

### 4. Inside VI, set the shell to bash using the following command:
```bash
:set shell=/bin/bash
```

### 5. Run the shell:
```bash
:shell
```
You should now be in a **normal bash shell** as bandit26.  

### 6. Retrieve the password as usual:
- Check current directory using `ls`
- Read the password file:
```bash
cat /etc/bandit_pass/bandit26
```
   
You now have Bandit26’s password, which you can safely save locally (unless you prefer repeating steps 1-5 ;)).  

---

## 💡 Bonus Tips  

- Ensure your terminal window is small enough to trigger the `--More--` prompt; the trick won’t work in a full-height terminal.  
- Pressing `v` in the pager always opens VI if available, letting you escape restricted shells.  
- Inside VI, `:set shell=/bin/bash` followed by `:shell` is a **general trick** for escaping some restricted environments.  

---

## 🧠 Why This Level Matters  

- Teaches **working with restricted SSH shells**.  
- Demonstrates how terminal behavior (`--More--` prompts) can be used to **break out into a full shell**.  
- Reinforces the value of **creative problem-solving** when normal commands appear blocked.  
