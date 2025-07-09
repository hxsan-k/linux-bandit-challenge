# Level 5 → 6 🗝️

---

## 🎯 Goal

Find the password for the next level, which is stored in a file **somewhere in the `inhere` directory** and is **human-readable**, **1033 bytes in size**, and **not executable**.

---

## 🛠 Commands Used

- `find` – Searches for files and directories  
- `file` – Tells you what kind of data a file contains  
- `cat` – Prints the contents of a file  
- `ls` – Lists files and directories  

---

## 🚀 How to Solve

1. First, go into the `inhere` directory:

```bash
cd inhere
```

2. Use `find` to locate a file that matches all the criteria:

```bash
find . -type f -size 1033c ! -executable
```

- `.` – Search from the current directory  
- `-type f` – Only return regular files  
- `-size 1033c` – File must be exactly 1033 bytes  
- `! -executable` – File must not be executable  

3. Confirm the file is human-readable by using:

```bash
file ./filename
```

(Replace `filename` with the actual result from `find`.)

4. If it says "ASCII text," display the contents:

```bash
cat ./filename
```

---

## 💡 Bonus Tips

- The `! -executable` flag is a simple way to filter out binaries or scripts.
- You can combine `find` with other commands using `-exec`, but this level keeps it simple.
- Try using `ls -lh` if you want a human-readable overview of file sizes.

---

## 🧠 Why This Level Matters

This level introduces the powerful `find` command with conditions, which is a core skill for sysadmins, developers, and security analysts alike. Being able to locate files based on specific criteria (like size or permissions) can save hours of manual searching and is often the first step in automation or forensic work.
