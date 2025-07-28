# Level 12 → 13 🗜️

---

## 🎯 Goal

The password for the next level is stored in the file `data.txt`, which is actually a **hexdump of a compressed file that’s been repeatedly compressed**. Our job is to reverse the process and extract the original file to reveal the password.

---

## 🛠 Commands Used

- `mkdir` – Creates a new directory  
- `mktemp -d` – Makes a temp directory with a random name  
- `cp` – Copies files  
- `mv` – Renames or moves files  
- `xxd -r` – Reverses a hexdump  
- `file` – Detects file type  
- `gzip`, `bzip2`, `xz` – Compression tools  
- `tar` – Extracts archive files  
- `cat` – Displays contents of a file  

---

## 🚀 How to Solve

1. First, create a safe working space:

```bash
cd /tmp
mktemp -d
cd <your-temp-folder>
```

2. Copy the data over and rename it:

```bash
cp /home/bandit12/data.txt .
mv data.txt data.hex
```

3. Reverse the hexdump back to binary:

```bash
xxd -r data.hex data.bin
```

4. Now, start inspecting the file to figure out its type:

```bash
file data.bin
```

This might say something like: `gzip compressed data`

5. Depending on the output, decompress using the correct tool. Rename it after each step to keep things clear:

```bash

mv data.bin data.gz
zcat data.gz > data1
file data1
```

6. Repeat this process: inspect the file with `file`, then apply the appropriate decompression command.

Examples:

- If it says bzip2, run: `bunzip2`
- If it says gzip, run: `zcat` or `gunzip`
- If it says POSIX tar, run: `tar -xf`
- If it says XZ, run: `unxz`
- Eventually, you’ll reach a file that just contains plain text — and that will have the password.

---

## 💡 Bonus Tips

- `file` is your best friend here. It tells you exactly how to proceed at each stage.
- Always rename files based on what `file` tells you. The compression tools won’t work if the file has the wrong extension.
- If a `tar` file extracts multiple files, check them all using `cat` or `file` to find the one with the password.

---

## 🧠 Why This Level Matters

This level is all about **recognising file formats and handling compression**, which are essential skills in system administration and CTF-style problem solving. You learn how to dissect files step-by-step, work safely in temporary directories, and identify file types like a Linux detective.
