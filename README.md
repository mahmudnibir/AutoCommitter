
# 📌 Commit Automation Script  

![GitHub Repo stars](https://img.shields.io/github/stars/mahmudnibir/AutoCommitter?style=social) 
![GitHub forks](https://img.shields.io/github/forks/mahmudnibir/AutoCommitter?style=social)
![GitHub contributors](https://img.shields.io/github/contributors/mahmudnibir/AutoCommitter)
![GitHub issues](https://img.shields.io/github/issues/mahmudnibir/AutoCommitter)
![GitHub last commit](https://img.shields.io/github/last-commit/mahmudnibir/AutoCommitter)
![GitHub license](https://img.shields.io/github/license/mahmudnibir/AutoCommitter)
![Node.js Version](https://img.shields.io/badge/Node.js-16%2B-brightgreen)
![GitHub Pull Requests](https://img.shields.io/github/issues-pr/mahmudnibir/AutoCommitter)
![GitHub Code Size](https://img.shields.io/github/languages/code-size/mahmudnibir/AutoCommitter)
![Platform](https://img.shields.io/badge/platform-linux%20%7C%20macOS%20%7C%20windows-blue) 

---
**⚠️ Note: This project is intended for learning and experimentation. Please use it responsibly and ethically.**

--- 
## 📚 Table of Contents  
- [Overview](#overview)  
- [Features](#features)  
- [Installation](#installation)  
- [Usage](#usage)  
- [How It Works](#how-it-works)  
- [Contribution](#contribution-guidelines)  
- [License](#license)  
- [Contact](#contact)  
- [Support](#support)
 


## Overview  

The **Commit Automation Script** is a Node.js tool that **automates Git commits** with randomized timestamps. This script is perfect for **filling up your GitHub contribution graph** or simulating commit history for testing purposes.  

✅ **Randomized Commit Dates** – Generates commits over a specific time period.  
✅ **Automated Git Process** – Adds, commits, and pushes changes seamlessly.  
✅ **Lightweight & Fast** – No unnecessary dependencies.  
✅ **Configurable Commit Count** – Adjust how many commits you want.  

---

##  Features  

| Feature | Description |
|---------|------------|
| 🔄 **Randomized Commits** | Automatically generates commits with random timestamps. |
| 🏗 **Fully Automated** | No manual intervention needed after execution. |
| 📅 **Custom Date Ranges** | Commits are spread over the past year (or user-defined range). |
| 🖥 **Easy to Use** | Just run the script and watch it work! |
| 🔧 **Customizable** | Modify commit count and frequency easily. |
| 🐙 **GitHub Integration** | Commits are automatically pushed to your remote repo. |

---

## Installation  

### **🔹 Prerequisites**  

Ensure you have the following installed:  

- **[Node.js](https://nodejs.org/en/)** (v16 or later)  
- **[Git](https://git-scm.com/)** (properly configured with a remote repository)  

### **🔹 Setup**  

Clone the repository and navigate into it:  

```bash
git clone https://github.com/mahmudnibir/AutoCommitter.git
cd AutoCommitter
```

Install dependencies:  

```bash
npm install jsonfile moment simple-git random
```

Run the script:  

```bash
node index.js
```

---

## Usage  

### **1️⃣ Customize Commit Count**  
Modify the number of commits in the script:  

```javascript
makeCommits(100); // Change 100 to any number of commits you want
```

### **2️⃣ Run the Script**  
Simply execute:  

```bash
node index.js  # Runs the script
```

### **3️⃣ View Commit History**  
Check the generated commits:  

```bash
git log --oneline --graph --decorate --all
```

---

## How It Works  
1️⃣ Generates a **random timestamp** (past year or custom range).  
2️⃣ Writes commit data to `data.json`.  
3️⃣ Uses `simple-git` to **stage, commit, and push**.  
4️⃣ Repeats until reaching the desired commit count.  
5️⃣ Enjoy a **fully automated commit streak!**  
 

---

## 📜 Code Breakdown  

### **1️⃣ `markCommit(x, y)` – Creates a Single Commit**  

```javascript
const markCommit = (x, y) => {
  const date = moment().subtract(1, "y").add(1, "d").add(x, "w").add(y, "d").format();
  jsonfile.writeFile(path, { date }, () => {
    simpleGit().add([path]).commit(date, { "--date": date }).push();
  });
};
```

✔️ **Generates a commit timestamp.**  
✔️ **Writes commit data to a JSON file.**  
✔️ **Commits and pushes changes to the repository.**  

### **2️⃣ `makeCommits(n)` – Recursively Generates Commits**  

```javascript
const makeCommits = (n) => {
  if (n === 0) return simpleGit().push();
  const x = random.int(0, 54);
  const y = random.int(0, 6);
  const date = moment().subtract(1, "y").add(1, "d").add(x, "w").add(y, "d").format();
  jsonfile.writeFile(path, { date }, () => {
    simpleGit().add([path]).commit(date, { "--date": date }, makeCommits.bind(this, --n));
  });
};
```

✔️ **Calls itself recursively to generate multiple commits.**  
✔️ **Randomizes commit timestamps for natural distribution.**  
✔️ **Stops when `n = 0` and pushes all commits.**  

---

## 📷 Example Output  

When running the script, it prints generated commit dates:  

```bash
2024-04-02T10:22:42+00:00
2024-06-16T10:22:42+00:00
2024-07-23T10:22:42+00:00
...
```

### ✅ **Git History Example (`git log --oneline --graph`)**  

```
* 8f3a1b4 (HEAD -> main, origin/main) 2024-07-23T10:22:42+00:00
* 7e2b9f6 2024-06-16T10:22:42+00:00
* 3a4c2e1 2024-04-02T10:22:42+00:00
```

---

## Contribution Guidelines  

💡 **Want to improve the script?** Contributions are welcome!  

### **📌 How to Contribute**  
| Step | Action |
|------|--------|
| 🏗 **Fork** | Clone the repo & create a new branch |
| 🔧 **Develop** | Make your changes, write clear commit messages |
| 📌 **Push** | Push to your fork & create a PR |
| 🚀 **Review** | Wait for approval & merge |


---

## License  

📝 This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.  

---

## Contact  
*Developed by [Nibir Mahmud](https://github.com/mahmudnibir)*


📧 **Email**: [nibirbbkr@gmail.com](mailto:nibirbbkr@gmail.com)  
🐦 **Github**: [@mahmudnibir](https://github.com/mahmudnibir)    

---

## Support  

If you find this project helpful, **please consider giving it a star ⭐ on GitHub!** It helps others discover the project.  

---
