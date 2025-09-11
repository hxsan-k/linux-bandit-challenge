# Level 8 → 9 🔁

---

## 🎯 Goal

The password for the next level is stored in the file `data.txt` and is the **only line that appears exactly once**.

---

## 🛠 Commands Used

- `sort` – Arranges lines in order (required by `uniq` command)
- `uniq` – Filters out duplicate lines or shows only unique ones (depending on the flag used)
- `cat` – Displays the content of a file
---

## 🚀 How to Solve

### 1. First, take a look at the file (optional):

```bash
cat data.txt
```

You’ll see a bunch of repeated-looking lines.

### 2. To find the line that only appears **once**, use a combination of `sort` and `uniq`:

```bash
sort data.txt | uniq -u
```

- `sort` is needed because `uniq` only works on **consecutive** duplicate lines  
- `uniq -u` filters out everything **except** lines that appear once

That line is the password.

---

## 💡 Bonus Tips

- You can pipe commands together using the pipe symbol `|` — it passes the output of one command into the next. In this case, `sort` feeds into `uniq`.
- Want to be sure your command worked correctly? Try adding `wc -l` at the end to count how many unique lines there are:

```bash
sort data.txt | uniq -u | wc -l
```
- You’re expecting the result to be 1, since the password is supposed to be the *only* unique line in the file.

---

## 🧠 Why This Level Matters

This level teaches how to combine commands using [**piping**](https://www.freecodecamp.org/news/linux-terminal-piping-and-redirection-guide/), a powerful way to work with [**data streams**](https://davidlares.medium.com/basic-data-streams-in-linux-b592a64518dd). Being able to filter, sort, and isolate useful information is vital in scripting, log analysis, and day-to-day command-line work. It’s a taste of what text processing in Linux is all about.

