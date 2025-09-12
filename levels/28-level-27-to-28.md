# Level 27 → 28 🔐

---

## 🎯 Goal  

Retrieve the contents of Bandit27’s Git repository to find the password for Bandit28.  
This level teaches how to **interact with a remote Git repository over SSH** using a custom port.  

---

## 🛠 Commands Used  

- `mkdir` – Create a directory  
- `cd` – Change into the directory  
- `git clone` – Clone a remote Git repository  
- `ls` – List files in a directory  
- `cat` – Read files  

---

## 🚀 How to Solve  

### 1. Log in as bandit27:
```bash
ssh bandit27@localhost -p 2220
```

### 2. **Make a directory to work in and ensure you are inside it:**  
```bash
mkdir /tmp/myrepo
```
```bash 
cd /tmp/myrepo
``` 

### 3. **Clone the repository from Bandit27’s Git user:**  
```bash
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
```
When prompted for a password, use **Bandit27’s password**.  

### 4. Verify that the repository has been cloned using `ls`:
   
You should see a directory named `repo`.  

### 5. Move into the repository and inspect its contents:
```bash
cd repo
```
```bash
ls
```
Look for a `README` file.  

### 6. Read the file to retrieve Bandit28’s password:
```bash
cat README
```
The output contains the password for Bandit28.  

---

## 💡 Bonus Tips  

- The Git repository is accessed via **SSH on port 2220**, so always include the port in the URL.  
- After cloning, you can navigate into any subdirectory and read files as usual.  

---

## 🧠 Why This Level Matters  

- Teaches **cloning Git repositories over SSH** with a custom port.  
- Reinforces **using credentials securely** to access remote repositories.  
- Provides practical experience in **retrieving sensitive information from version-controlled files**.  
