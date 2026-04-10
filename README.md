# Linux-Log-File-Analysis-Automation-and-SIEM-Visualization

# Project 1: Manual Log Analysis (SOC Workflow)

##  About this Project
In this project, I stepped into the shoes of a **SOC (Security Operations Center) Analyst** to learn how to spot suspicious activity within computer logs. The goal was simple but essential: monitor a system, detect anomalies, and analyze potential threats like brute-force attacks.

By doing this manually, I gained a much deeper understanding of how system logs work and why they are the first line of defense in cybersecurity.

##  What I used
* **Dataset:** Linux authentication logs from LogHub (`Linux_2k.log`).
* **Editor:** VS Code (to review and highlight the raw log files).
* **Analysis:** Google Sheets / Excel (to organize and make sense of the data).

---

## 🔍 Step-by-Step Process

### Step 1: Getting the Data
I started by downloading the `Linux_2k.log` dataset. This file is great because it simulates a real-world Linux environment, filled with user sessions, system events, and—most importantly—authentication attempts.

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


### Step 2: First Look & Review
I opened the file in **VS Code** to keep things organized. To keep the analysis focused and high-quality, I decided to focus on the first **20 to 40 lines**. This helped me get familiar with the log structure without getting overwhelmed by thousands of lines of data.

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx



### Step 3: Hunting for Red Flags
I carefully scanned the entries looking for "red flags" that suggest a system is under attack. I specifically looked for:
* **Failed logins** coming repeatedly from the same IP address.
* Attempts to log in using **invalid or unknown usernames**.
* **Abnormal system exits** or alerts.

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


**Why does this matter?** These patterns usually mean someone (or a bot) is trying to brute-force their way into the system or looking for non-existent users to exploit.

### Step 4: Documentation
I made it a goal to log between **10 and 20 specific entries** from my initial sample. By focusing on this smaller set, I was able to practice a real SOC workflow (**Monitor → Detect → Analyze**) while ensuring I truly understood what each line of the log was telling me.

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx


---

## 💡 Key Takeaway
This exercise taught me that security isn't just about automated tools; it's about knowing what "normal" looks like so you can spot the "suspicious."
