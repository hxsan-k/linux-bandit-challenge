# Level 32 → 33 🔐

## 📝 Level Goal  
After all the git challenges, this level throws you into a strange shell where normal commands don’t seem to work. Your goal is still the same: find the password for the next level.  

---

## 🚀 How to Solve  

### 1. Notice the restricted shell:

When you log into `bandit32`, you don’t land in a normal bash shell. 
  
Instead of the usual `banditX@bandit:` you see a strange symbol like this:

```bash
>>
```
  
Try playing around with basic commands like `ls` or `cat`, and you'll see it gives you errors such as `Permission denied`.  

### 2. Use `$0` to escape into a real shell:
    
The trick here is that `$0` represents the current shell process. Running it directly can drop you into a *“real”* shell.  

```bash
$0  
```

Now your prompt changes to a regular `$`.  

### 3. Run normal commands inside the new shell:

From here, you can use all the usual Linux commands again.  
  
To get the password, simply type:
  
```bash
cat /etc/bandit_pass/bandit33  
```
  
That’s the password for **bandit33**. 🎉  

---

## 💡 Bonus Tips  
- `$0` is a special variable that stores the name of the current shell process. Executing it effectively "re-invokes" your shell.  
- This puzzle is all about recognising that you’re trapped in a restricted environment and finding a creative way out.  

---

## 🔑 Why This Level Matters  

- This challenge shows how important it is to understand **how shells work** if you want to find "cracks" in them.
- Even when you’re restricted by filters or strange behavior, you can sometimes use weird tricks to break free.
- It’s a great intro to bypassing restricted shells in the real world.  
