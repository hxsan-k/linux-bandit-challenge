# Level 1 → 2 🔐

---

## 🎯 Goal

The password for the next level is stored **inside a file called `-`** located in the home directory.

---

## 🛠 Commands Used

- `ls` – Lists files in the current directory.
- `cat` – Prints the contents of a file.
- `./` – Used to reference a file or command in the current directory.

---

## 🚀 How to Solve

The tricky part here is the filename: `-`.  
Normally, `-` is treated as a flag in most commands, so trying `cat -` won’t work how you'd expect as it waits for user input instead.

To get around this, you need to tell the system ***"this is a file, not a flag"*** by using `./` before the name:

```bash
cat ./-
```

This reads the file named `-` from the current directory.

---

## 💡 Bonus Tips

- `-` is a common placeholder for standard input/output, which is why commands can get confused.
- `./` explicitly refers to the current directory, helping avoid this issue.
- You can also use `--` with many commands to stop flag parsing (e.g. `cat -- -`), but `./-` is usually simpler.
> 👉 Flag parsing is when a command looks at inputs that start with `-` and treats them as special options instead of filenames. Using `--` tells the command: *“stop treating things as options. Just read them as-is.”*

---

## 🤔 Why This Level Helps

You’ll come across weird filenames in real systems, especially when testing, scripting, or dealing with automated tools.  
Understanding how to handle them properly saves you from a lot of confusion later on.

