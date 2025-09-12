# Level 29 → 30 🔐  

---

## 🎯 Goal  

We need to retrieve the password for **bandit30** from a Git repository. Unlike previous levels where the password was hidden in old commits, this time the hint says *“no passwords in production”*, so the credentials are stored in a different Git branch.  

---

## 🛠 Commands Used  

- `git clone` – Copy the repository  
- `git branch -a` – View all branches  
- `git checkout` – Switch to another branch  
- `cat` – Read files  

---

## 🚀 How to Solve  

### 1. Like previous steps, clone the repository into a temporary directory which you create:

```bash
mkdir /tmp/myrepo29  
cd /tmp/myrepo29  
git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo  
```

Enter the **bandit29 password** when prompted.  

### 2. Inspect the README on the master branch:
```bash
cd repo  
cat README.md  
```

It shows credentials, but the password field says `<no passwords in production!>`.  

### 3. Check available branches:
```bash
git branch -a  
```
  
You’ll see extra branches such as `origin/dev` and `origin/sploits-dev`.  

### 4. Switch to the development branch: 

```bash
git checkout origin/dev  
```
  
Now list the files and open `README.md` again.  

### 5. Retrieve the password:  

```bash
cat README.md  
```
  
Inside the `dev` branch, the README contains the actual password for **bandit30**. 🎉  

---

## 🔢 Step-by-Step Explanation  

- The **master branch** is the production version, where the password is intentionally hidden.  
- Running `git branch -a` reveals additional branches, which represent alternate “timelines” of the repository.  
- By switching to `origin/dev`, you view the development environment where credentials are still present.  
- Reading `README.md` in this branch reveals the password for bandit30.  

---

## 💡 Bonus Tips  

- Think of Git branches as **different environments**: production, development, and experimental.  
- `master` is clean and ready for deployment, while other branches may contain secrets or work-in-progress changes.  
- Always explore branches when hunting for hidden information in Git repos.  

---

## 🧠 Why This Level Matters  

This level shows the importance of understanding **branching in Git**. Secrets or sensitive data are often removed from production but left behind in development or feature branches.  

You learn to:  
- Use `git branch` and `git checkout` effectively  
- Recognize how developers separate production and development environments  
- Apply branching knowledge in security investigations  
