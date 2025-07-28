# Level 13 → 14 🔐

---

## 🎯 Goal

Use the **private SSH key** stored in `sshkey.private` to log in to the next level (Bandit14). No password this time — just the key.

---

## 🛠 Commands Used

- `ssh -i` – Log in with a private SSH key  
- `chmod` – Change file permissions  
- `ls -al` or `ls -hl` – View file permissions  

---

## 🚀 How to Solve

1. Try logging in using the SSH key:
```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```
You’ll likely see this error:

`Unprotected private key file`

That’s Linux being overprotective (but for good reason).

2. Check the permissions on the key:
```bash
ls -hl
```

If it looks something like this:

`-rw-r--r--` 

That means:
  - Owner can **read and write**
  - Group can **read**
  - Others can **read**

That’s way too open for a private key.

3. Fix it with:
```bash
chmod 400 sshkey.private
```

This sets permissions to:
`-r--------`  

Which means:
  - ✅ You (the owner) can **read**
  - ❌ No one can **write to** or **execute** it  
  - 🔒 Everyone else is completely blocked

4. Try the SSH command again — it should let you in now.

5. Find the password using `cat`, which is stored in /etc/bandit_pass/bandit14

---

## 🔢 Quick Explanation: `chmod` Numbers and Permission Strings

Linux permission strings are 10 characters long. The first character shows the file type, and the remaining 9 characters are split into 3 groups of 3 where:
- `-` indicates type: `-` is a file, `d` is a directory (there are others, but these are the most common)
- `o` represents owner's permissions
- `g` represents group's permissions
- `w` represents "world", or all other users' permissions

Each digit is a sum of:
- 4 = read (r)  
- 2 = write (w)  
- 1 = execute (x)

So using the owner as an example:
- `7` = 4 + 2 + 1 = read, write, and execute (or `-rwx------` which means read, write, execute is allowed)
- `6` = 4 + 2 = read and write (`-rw-------`)
- `5` = 4 + 1 = read and execute (`-r-x------`)  
- `4` = read only (`-r--------`)
- `0` = no permission  

### Why `chmod 400`?

We want:
- Owner: read only → `4`  
- Group: no access → `0`  
- Others: no access → `0`

Result: `chmod 400`

This locks down the key so SSH trusts it.

---

## 💡 Bonus Tips

- Private keys need to be **private**. If anyone else can read or write to them, they’re not secure anymore.  
- `chmod 400` is standard practice when using SSH keys on Linux systems.  

---

## 🧠 Why This Level Matters

This level teaches you how **SSH authentication with keys** works, and how Linux cares deeply about **file permissions** when it comes to security. Even if you have the right key, it won’t work unless the permissions are strict enough.

Get used to seeing `chmod 400` whenever SSH keys are involved.
