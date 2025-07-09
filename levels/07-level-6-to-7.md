# Level 6 → 7 🔍

---

## 🎯 Goal

The next password is stored ***somewhere on the server*** according to the instructions.

We are given some key details which will help us solve this. The file is:

- Owned by **user** `bandit7`
- Owned by **group** `bandit6`
- Exactly **33 bytes** in size

---

## 🛠 Commands Used

- `find` – Search for files and directories based on conditions
- `cat` – Read the contents of a file

---

## 🚀 How to Solve

1. Since the file could be anywhere, we’ll start at the root directory:

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
- `/` – To tell the command to search the whole system, starting from the very top
  > This can be slow for obvious reasons. Replace `/` with `.` when you know which folder you're supposed to be in. `.` searches *just* the current folder instead.

- `-type f` – Only look for files

- `-user bandit7` – Owned by the correct user

- `-group bandit6` – Owned by the correct group

- `-size 33c` – Exactly 33 bytes in size

- `2>/dev/null` – Ignore permission denied errors to keep the output clean

> 📝 Note: The `2>/dev/null` part isn't required and the command still works without it. It just hides all the *"Permission denied"* messages from folders you don’t have access to, making the output easier to read.

2. Once you find the correct file, use `cat` to read the password:

```bash
cat /path/to/the/file
```
## 💡 Bonus Tips
- You will get a lot of `"permission denied"` errors if you don’t use `2>/dev/null`. This is normal as you don’t have access to most things on the server.

- `find` can be overwhelming at first, but it's one of the most powerful tools in Linux for digging through files.

## 🧠 Why This Level Matters

This level is a great intro to more advanced file searches. It teaches you how to filter files based on multiple conditions which is useful when managing systems, tracking down logs, or doing security audits.
