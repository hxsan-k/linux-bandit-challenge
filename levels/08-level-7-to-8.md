# Level 7 → 8 📄

---

## 🎯 Goal

The password for the next level is stored in the file `data.txt`, **next to the word `millionth`**. This level serves as a good intro to the powerful `grep` command.

---

## 🛠 Commands Used

- `grep` – Searches for patterns inside text  
- `cat` – Displays the contents of a file  

---

## 🚀 How to Solve

### 1. The file `data.txt` is already in the current directory. We’re looking for the line that contains the word `millionth`.

Use `grep` to filter only the relevant line:

```bash
grep millionth data.txt
```

This returns the line containing the word `millionth` and the password right next to it.

### 2. Alternatively, if you want to see the whole file first (not necessary here):

```bash
cat data.txt
```

But in this case, `grep` is faster and cleaner.

---

## 💡 Bonus Tips

- `grep` is a powerful tool for searching inside files. You can also use flags like `-i` for case-insensitive or `-r` for recursive searches through folders.
- If the format had been different (e.g. the word `millionth` was on one line and the password on the next), you might need more advanced tricks like `awk`, `sed`, or `grep -A1`.

---

## 🧠 Why This Level Matters

This level introduces the idea of **text pattern searching**, which is key in almost every Linux task, from finding log entries to processing datasets. Knowing how to extract specific lines or values quickly is a must-have skill for automation, scripting, and system investigation.
