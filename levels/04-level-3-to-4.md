# Level 3 → 4 🕵️‍♂️

---

## 🎯 Goal  

Find the password for **bandit4** which is stored in a **hidden file** inside the `inhere` directory.

---

## 🛠 Commands Used  
- `ls` – Lists files in the current directory  
- `ls -a` – Lists **all** files, including hidden ones (those starting with a dot `.`)  
- `cd` – Changes directory  
- `cat` – Prints the content of a file

---

## 🚀 How to Solve

### 1. First, move into the `inhere` directory:
```bash
cd inhere
```

### 2. Run `ls` 

You won’t see anything as the file is hidden.

### 3. Use the `-a` flag to reveal hidden files:
```bash
ls -a
```

You’ll see something like this on your screen:
```
.  ..  .hiddenfile
```

### 4. Use `cat` to view the contents of the hidden file:
```bash
cat .hiddenfile
```

The output will be the password for **Level 4**.

---

## 💡 Bonus Tips
- Hidden files in Linux always begin with a `.` — keep this in mind for future levels.
- `ls -a` is your best friend when a file “seems” to be missing.
- You can combine commands for speed:  
  e.g. `cat inhere/.hiddenfile`
> Even when you find the password, try playing around with commands and combinations to see if there were other ways of solving the problem you had. It’s one of the best ways to get used to how Linux works and it will help you in later levels. 

---

## 🧠 Why This Level Matters
Learning how to deal with hidden files is important for navigating Linux systems, especially when working with config files or debugging odd issues.

