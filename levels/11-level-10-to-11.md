# Level 10 → 11 🔐

---

## 🎯 Goal

The password is hidden in `data.txt`, which contains **Base64‑encoded** text.

---

## 🛠 Commands Used

- `base64` – Encodes or decodes Base64 data (`-d` flag for decode)
- `cat` – Displays file contents 

---

## 🚀 How to Solve

### 1. `cat` the file to confirm it looks like Base64:

```bash
cat data.txt
```

You’ll see long lines ending with `=` or `==`, a classic Base64 tell‑tale.

### 2. Print the result again but a piping symbol to attach the base64 decode command:

```bash
cat data.txt | base64 -d
```

The output reveals the password.

---

## 💡 Bonus Tips

- If you’re ever unsure whether a file is Base64, try `file data.txt` - it usually guesses correctly.
- `base64` defaults to **encode** mode; remember the `-d` (or `--decode`) flag to reverse the process.

---

## 🧠 Why This Level Matters

Base64 pops up everywhere: API tokens, email attachments, config blobs and so on. Being able to decode it quickly is indispensable. This level reinforces the habit of recognising encoded data and turning it back into something readable with a single command.
