# Level 18 → 19 🔐

---

## 🎯 Goal  

The next password is sitting in a file called `readme` in your home directory.  
The tricky part? Someone has messed with `.bashrc` so that if you try to log in normally via SSH, it immediately logs you out, so we need to "grab" the password before it does that.

---

## 🛠 Commands Used  

- `ssh` – Log in to the server  
- `ls` – List files in a directory  
- `cat` – View the contents of a file  

---

## 🚀 How to Solve  

1. The first challenge is that `.bashrc` automatically logs you out when using SSH.

To bypass this, you can use a command that runs **directly on login** instead of opening a shell:  
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 ls -l
```

This lets you see the files in the home directory without triggering the logout.  

2. Confirm that the `readme` file exists using the same command above.
   
You should see something like:  
```bash
-rw-r--r-- 1 bandit18 bandit18 33 Aug 29 20:00 readme
```

3. Read the contents of `readme` to get the password:  
```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

The output will be the password for Bandit19.  

---

## 🔢 Quick Explanation  

- By passing a command in quotes to `ssh`, you **run that command directly** on the server instead of opening an interactive shell.  
- This is a common trick when `.bashrc` or `.profile` scripts interfere with login.  
- `ls` helps you see the files, and `cat` lets you read the password without actually entering a shell.  

---

## 💡 Bonus Tips  

- Always check the home directory first; `readme` is usually where Bandit stores next-level passwords.  
- Using `ssh` with a command in quotes is a handy way to bypass login scripts or forced logouts.  
- Remember: the logout is part of the challenge — don’t try to fix `.bashrc` manually.  

---

## 🧠 Why This Level Matters  

This level teaches you how to:  

- Handle situations where interactive login is blocked  
- Use `ssh` to execute commands remotely without a shell  
- Efficiently read files and extract information in tricky scenarios  
