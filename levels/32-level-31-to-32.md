# Level 31 → 32 🔐

## 📝 Level Goal  
This level tests your Git skills in a slightly different way. You need to **push a file to a remote repository** in order to receive the next password. The challenge includes a `.gitignore` that blocks the file name you need to push.  

---

## 🛠 Commands Used  
- `git clone` – Clone the remote repository locally  
- `mkdir` – Create a temporary working directory  
- `echo` – Generate the file contents  
- `git add -f` – Force-add files that are ignored by `.gitignore`  
- `git commit` – Commit changes to the local repository  
- `git push` – Push changes to the remote repository  

---

## 🚀 How to Solve  

**1. Like previous steps, clone the repository into a temporary directory**  

  ```bash
    mkdir /tmp/myrepo31  
    cd /tmp/myrepo31  
    git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo   
  ```
  Enter the **bandit31 password** when prompted. 
  
**2. Move into the cloned repository and `cat` the `README.md` file**  

  ```bash
    cd repo  
    ls  
    cat README.md
  ``` 
  This shows you the task: create a file `key.txt` containing `May I come in?` and push it to the `master` branch.  

**3. Create the file with the required contents** 

  ```bash
    echo 'May I come in?' > key.txt  
  ```

**4. Force-add the file to Git** 

  ```bash
    git add -f key.txt  
  ```
  The `-f` flag is necessary because `.gitignore` prevents normal `git add` for this file.  

**5. Commit the change**

  ```bash
    git commit -m "adding key.txt"
  ```

**6. Push the change to the remote repository**

  ```bash
    git push origin master
  ```
  You may be prompted for the **bandit31-git password** (same as bandit31’s password).  

  Even though the push is ultimately rejected by a pre-receive hook, the remote runs a validation script and returns the password for **bandit32**.

---

## 💡 Bonus Tips  
- `.gitignore` can block files from being added — `git add -f` overrides it.  
- You don’t need the push to actually succeed; the server reveals the password before rejecting it.  
- Always check README files for instructions — the exact file name, contents, and branch are specified there.  

---

## 🔑 Why This Level Matters  
This level teaches:  
- How to work with `.gitignore` and force-add ignored files  
- The Git workflow for committing and pushing changes  
- How to interact with remote repositories in controlled environments  

It reinforces that even when restrictions exist, there are ways to satisfy requirements and retrieve the needed information.
