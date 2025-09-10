# Level 28 → 29 🔐

---

## 🎯 Goal  

Retrieve the password for Bandit29 by interacting with Bandit28’s Git repository.  
This level teaches how to **examine Git history and check out previous commits** to access hidden information.  

---

## 🛠 Commands Used  

- `mkdir` – Create a directory  
- `cd` – Change into the directory  
- `ls` – List files in a directory  
- `cat` – Read files  
- `git log` – View commit history
- `git clone` – Clone a remote Git repository  
- `git checkout` – Switch to a previous commit  

---

## 🚀 How to Solve  

1. **Make a temporary working directory and move into it:**  
    ```bash
    mkdir /tmp/myrepo
    ```
    ```bash 
    cd /tmp/myrepo
    ```

2. **Clone Bandit28’s Git repository:**  
    ```bash
    git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
    ``` 
    - When prompted, enter **Bandit28’s password**. 

3. **Verify the repository, move into it, and cat the README file as you did in the previous level:**  
    ```bash
    ls
    ``` 
    ```bash 
    cd repo
    ```
    ```bash
    cat README.md
    ```
    - You will likely see the password as `xxxxxxxxx`.
    - The password should be in a previous version...

4. **Check the Git commit log:**  
    ```bash
    git log
    ```
    - Examine the commits and look for hints like “add missing data” or older versions of files.  
    - Note the **hash of the previous commit** where the password is visible.  

5. **Check out the previous commit using its hash:**  
    ```bash
    git checkout <previous commit hash>
    ```

6. **Verify the files in the older commit again using `ls`:**  
    - You should see the same `README.md` file again.  

7. **Read the README file in the older commit to retrieve Bandit29’s password:**  
    ```bash
    cat README.md
    ``` 
    - The output contains the password for Bandit29.  

---

## 💡 Bonus Tips  

- Use `git log --oneline` for a shorter commit history if the repository has many commits (not required here).  
- You can switch back to the latest commit anytime with `git checkout main` or `git checkout master`.  
- Always verify the content after checking out an older commit; some files may not exist or may have changed.  

---

## 🧠 Why This Level Matters  

- Demonstrates **examining Git history** to find hidden information.  
- Teaches the use of **`git checkout` to access previous versions** of files.  
- Provides practical experience in **retrieving sensitive information from version-controlled files** and understanding how commits can change repository content.  
