# Level 0 → 1 🔐

---

## 🎯 Goal

Find the password for the next level.

The password for `bandit1` is stored in a file called `readme` located in the home directory.
> 💡 Remember: You're already logged in as `bandit0`. If not, SSH back in using `bandit0`.

---

## 🛠 Commands Used

- `ls` – Lists files in the current directory
- `cat` – Prints the content of a file to the screen

> 💡 You might see `ls -a` used in other levels to show hidden files, but for this one, `ls` is enough.

---

## 🚀 How to Solve

### 1. Use `ls` to see what files are in your current directory:

```bash
ls
```

### 2. You’ll see a file named `readme`. Use `cat` to read its contents:

```bash
cat readme
```

### 3. The output will be the password you need to log into **Level 1 ** (`bandit1`).

---

## 💡 Bonus Tips

- If `ls` doesn’t show anything, try `ls -a` to reveal hidden files (not needed here, but useful in future levels).
- Remember, Linux is case-sensitive — make sure you type file names exactly.

---

## 🧠 Why This Level Matters

This is your first taste of basic Linux file navigation.  
Knowing how to explore directories and read file contents is essential for working with any system.

