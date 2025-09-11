# Level 4 → 5 🔎

---

## 🎯 Goal

Find the password which is stored in the only ***human-readable*** file in the `inhere` directory.

---

## 🛠 Commands Used

- `ls` – Lists files in a directory  
- `file` – Tells you what kind of data a file contains  
- `cat` – Prints the content of a file to the screen  

---

## 🚀 How to Solve

### 1. First, go into the `inhere` directory:

```bash
cd inhere
```

### 2. List the files:

```bash
ls
```

You’ll see a list of different files like `-file00,` `-file01,` etc.

### 3. Use the `file` command to check which one is human-readable (look for "ASCII text"):

```bash
file ./*
```

### 4. Once you find the ASCII text file, display its contents:

```bash
cat ./-file0X
```

(Replace `-file0X` with the actual file name)

## 💡 Bonus Tips

- Use `./` in front of filenames that start with `-` so the shell doesn't mistake them for options (e.g. `./-file00`)
- Alternatively, you can run:

```bash
cat -- -file00
```
The `--` tells the command to stop parsing flags (a.k.a. options)

> Flag parsing is when the command interprets things like `-v` or `--help` as special options. Using `--` stops that.

## 🧠 Why This Level Matters

You’ll often run into files that aren’t human-readable or use weird naming conventions. Knowing how to figure out what kind of file you’re dealing with and how to safely open it is incredibly useful, especially in real-world debugging situations.
