# Level 11 → 12 🔐

---

## 🎯 Goal

The password for the next level is stored in `data.txt`, where all **letters** (both lowercase and uppercase) have been **rotated 13 positions** in the alphabet (ROT13).

---

## 🛠 Commands Used

- `cat` – Displays file contents  
- `tr` – Translates (substitutes) characters from one set to another

---

## 🚀 How to Solve

### 1. Start by displaying the contents of the file:

```bash
cat data.txt
```

You’ll see a string of text that looks random because it’s ROT13 encoded. It’s not encryption, just a basic letter substitution where each letter is shifted 13 places forward.

### 2. To decode it, use the tr (translate) command:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```
This will translate the scrambled text into readable characters and reveal the password.

---

## 🔍 Understanding the tr Command

### 🧾 Basic Syntax

```bash
tr 'from' 'to'
```

This means:

- Replace each character in the 'from' set with the corresponding character in the 'to' set, one-to-one, in order.
- The 1st character in 'from' is replaced by the 1st character in 'to', the 2nd with the 2nd, and so on.

So here:

```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### `A-Za-z` represents the full alphabet:
- A-Z = all uppercase letters
- a-z = all lowercase letters

### `N-ZA-Mn-za-m` is the same alphabet, but rotated 13 positions forward:

- `N-ZA-M` shifts uppercase letters:
  - A → N, B → O, ..., M → Z
  - Then wraps around: N → A, ..., Z → M
- `n-za-m` does the same for lowercase letters

📌 In short, it performs a ROT13 transformation, which is a simple form of letter substitution.

---

## 💡 Bonus Tips
- ROT13 is its own reverse. If you run the same command again on the decoded string, it’ll go back to the scrambled version.
- This method isn’t used in real-world cryptography, but it’s handy for understanding how basic character substitutions work.
- `tr` is a powerful tool beyond ROT13, as it can be used to:
  - Convert lowercase to uppercase
  - Remove or squeeze repeated characters
  - Replace or delete specific characters in a stream

---
 
## 🧠 Why This Level Matters
- Encourages recognising obfuscation (ROT13) and using the right tools to reverse it
- Reinforces command-line text manipulation using `tr`
