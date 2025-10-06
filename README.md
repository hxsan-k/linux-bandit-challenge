# Linux Bandit Challenge Walkthrough 🐧

This repo contains my notes, solutions, and lessons learned from completing the OverTheWire Bandit wargame. 

The goal was to build practical Linux command line skills with no prior tech background, and to serve as a guide for anyone else beginning their journey into Linux fundamentals.  

By documenting each level, I’ve aimed to make the solutions clear, reproducible, and beginner-friendly, while also highlighting the key concepts learned along the way.

---

## 📘 About the Challenge  

- The goal of each level is to find the password (or key) that unlocks the next.  
- Passwords are usually long strings of characters, but some levels use `ssh` private keys instead.  
- Levels get progressively harder, covering everything from basic file navigation to more advanced Linux tools.  
- The challenge is hands-on and incremental, designed to build confidence step by step as the puzzles grow more complex.

---

## 📁 What’s in This Repo  

- `levels/` — contains all Bandit walkthroughs, one file per level.
- Each level write-up shows the step-by-step process I used to solve it.
> [!TIP]
> Before checking solutions, attempt the level on your own and use each step as a hint in the right direction when needed.

---

## 🧠 New to Linux? Read This First  

- **Don’t panic** when the terminal looks empty, or when the output looks confusing. That’s normal.
- **Use `man`, `--help`, or Google** to understand commands and how to use them - you don’t need to memorise everything.
- **Get comfortable with the basics**: `ls`, `cd`, `cat`, `find`, `file`, and `grep` will take you far.
- **Remember to make a note of each password.**
- **Make notes on commands as you go.** When you finally crack the code with a command, type/write it down for memory.
- **Consider downloading Ubuntu on WSL if you're on Windows** - it gives you a real Linux environment right inside Windows.

> [!IMPORTANT]
> Before you start, I highly recommend watching this guide to mastering Linux man pages. It will be invaluable throughout the challenge and make you less dependant on Google and AI:
> 
> [Mastering Linux man pages (YouTube)](https://www.youtube.com/watch?v=RzAkjX_9B7E)

---

## 🛠️ How to Install WSL (Windows Subsystem for Linux)

**1. Open PowerShell as Administrator**  
- Click the Start menu, search for **Windows PowerShell**, then right-click and choose **Run as Administrator**.

**2. Run the install command**  
   ```powershell
   wsl --install
   ```

- This will install WSL along with Ubuntu by default. You may be prompted to restart your computer.

**3. Set up your Linux user**

- After restarting, Ubuntu will launch automatically and ask you to create a username and password.

You’re now ready to start using Linux on Windows!

If you're considering the challenge, want to talk about how you found it, or even need help just SSHing into the game for the first time, feel free to message me on LinkedIn!

---

## 🔗 Connect with Me

### Feel free to connect or message me here:  
#### [LinkedIn – Hasan Kamran](https://www.linkedin.com/in/hasankamrandev)
