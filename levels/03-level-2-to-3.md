# Level 2 → 3 🔐

---

## 🎯 Goal

Find the password for the next level stored in a file with spaces in its name, located in the home directory.

---

## 🛠 Commands Used

- `ls` – Lists files in the current directory  
- `cd` – Changes directory  
- `cat` – Displays file content

---

## 🚀 How to Solve

Files with spaces in their names can be tricky to work with in the terminal. To handle them, you need to either:

- Wrap the filename in quotes like `"spaces in this filename"`, or  
- Escape the spaces with backslashes like `spaces\ in\ this\ filename`

The first solution might feel intuitive if you’ve used programming or scripting languages like Python or Bash before, where quoting strings or escaping characters is common.

Once you identify the file, use `cat` as normal (with the correct quoting) to read the file contents.

---

## 💡 Bonus Tips

- Use `ls` or `ls -a` to list all files, including hidden ones.
- Remember, Linux is case-sensitive.  
- Quoting or escaping spaces prevents the shell from interpreting parts of the filename as separate arguments.  
> If you try `cat spaces in this filename` without surrounding it with quotations, you'll see how the terminal treats each word as a separate argument.
---

## 🧠 Why This Level Matters

Working with filenames that contain spaces is common in real-world scenarios. Learning to handle these properly helps avoid frustrating errors and makes command-line work smoother.
