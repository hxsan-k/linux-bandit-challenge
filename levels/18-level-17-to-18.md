# Level 17 → 18 🔐

---

## 🎯 Goal  

Find the password for the next level by comparing two files in your home directory: `passwords.old` and `passwords.new`.  
The password for Bandit18 is the **only line that has changed** between the two files.  

---

## 🛠 Commands Used  

- `ls` – List files in the directory  
- `diff` – Compare two files line by line  
- `cat` – View file contents  

---

## 🚀 How to Solve  

1. List the files to confirm they exist:  
```bash
ls
```

You should see two files:  
```bash
passwords.old  passwords.new
```

2. Compare the files using `diff`:  
```bash
diff passwords.old passwords.new
```

The output will look something like this:  
```bash
< abcdefghijklmnopqrstuvwx
---------------------------
> ZYXWVUTSRQPONMLKJIHGFEDCBA
```

3. Understand the output and `diff` arrows:  

- `<` → line from the **first file** (`passwords.old`)  
- `>` → line from the **second file** (`passwords.new`)  

Since the password is in `passwords.new`, the line after `>` is the password for Bandit18.  

4. Copy the line after `>` to use as your password for the next level.  

---

## 🔢 Quick Explanation: diff  

- `diff` compares two files line by line and highlights differences.  
- The `<` arrow shows what exists in the first file but not in the second.  
- The `>` arrow shows what exists in the second file but not in the first.  

This makes it very easy to spot the one line that changed.

---

## 💡 Bonus Tips  

- `diff` is faster than scanning manually or using `grep` in this scenario.  
- Always check which file the arrow points to; the next password is always in `passwords.new` (`>`). 

---

## 🧠 Why This Level Matters  

This level teaches you how to:  

- Compare files efficiently using `diff`  
- Interpret the `<` and `>` arrows to understand file differences  
- Quickly extract specific information from a large file

Now, on to the next!
