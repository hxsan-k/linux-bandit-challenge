# Level 30 → 31 🔐  

---

## 🎯 Goal  

Retrieve the password for **bandit31** by inspecting the Git repository. Unlike previous levels where the answer was in a branch or commit, here it’s hidden inside a **tag**.  

---

## 🛠 Commands Used  

- git clone – copy the repo locally  
- git tag – list all available tags in the repo  
- git show <tag> – display details (message, content) of a given tag  

---

## 🚀 How to Solve  

**1. Clone the repository**  

Clone the repo into a temporary directory like before:  

  ```bash
  git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo  
  ```

Enter the **bandit30 password** when prompted.  

**2. Move into the repo**  

  ```bash
  cd repo  
  ```

**3. Look for tags**  
  
  ```bash
  git tag  
  ```

This lists tags associated with the repo.  

**4. Inspect the tag contents**  

Pick the tag you found and run:  

  ```bash
  git show <tagname>    
  ```

One of the tags reveals the **password for bandit31**.  

---

## 💡 Bonus Tips  

- Tags in Git are like labels for specific commits — they often mark important states like releases.  
- Unlike branches (which move as development continues), tags always stick to the exact commit they were created on.  
- Always check for **branches, logs, and tags** when digging for hidden info in Git repos.  

---

## 🧠 Why This Level Matters  

This challenge shows that sensitive information can be hidden in **tags**, not just files or commit history. It reinforces the idea of exploring **all parts of a Git repo** when investigating code or auditing for secrets.  
