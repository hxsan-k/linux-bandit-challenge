# Level 9 → 10 🧬

---

## 🎯 Goal

The password is hidden in the file `data.txt` and appears as a **human-readable string,** following **several `=` characters.**

---

## 🛠 Commands Used

- `strings` – Extracts readable text from binary or non-text files  
- `grep` – Searches for matching patterns in text  
- `cat` – Displays file contents (optional)

---

## 🚀 How to Solve

### 1. First, check what's inside the file (optional):

```bash
cat data.txt
```

The file is mostly unreadable, which means it's likely a binary file. So we need to extract only the **readable parts.**

### 2. Use `strings` to pull out all human-readable content:

```bash
strings data.txt
```

This shows just the readable ASCII text while ignoring the binary junk.

### 3. Now, filter for lines containing at least 2 `=` symbols (since the password appears after several `=` signs):

```bash
strings data.txt | grep ==
```

This narrows down the result to a few lines. The one with the password should stand out clearly.

---

## 💡 Bonus Tips

- `strings` is useful for reverse engineering or pulling clues from corrupted or binary files (a helpful trick in CTFs and security work).

---

## 🧠 Why This Level Matters

This level shows how to work with **non-text files**, where normal tools like `cat` or `grep` won't help directly. Tools like `strings` are essential for extracting usable data from binary or compiled files. This is a common need in debugging, digital forensics, and security analysis.
