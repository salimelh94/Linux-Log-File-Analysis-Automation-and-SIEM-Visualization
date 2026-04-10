# Linux-Log-File-Analysis-Automation-and-SIEM-Visualization

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/3871186e81c115899b2ab3eb1cad1f2a972ca9ca/images/5nSIK.jpg)

# Project 1: Manual Log Analysis (SOC Workflow)

##  About this Project
In this project, I stepped into the shoes of a **SOC (Security Operations Center) Analyst** to learn how to spot suspicious activity within computer logs. The goal was simple but essential: monitor a system, detect anomalies, and analyze potential threats like brute-force attacks.

By doing this manually, I gained a much deeper understanding of how system logs work and why they are the first line of defense in cybersecurity.

##  What I used
* **Dataset:** Linux authentication logs from LogHub (`Linux_2k.log`).
* **Editor:** VS Code (to review and highlight the raw log files).
* **Analysis:** Google Sheets / Excel (to organize and make sense of the data).

---

## Step-by-Step Process

### Step 1: Getting the Data
I started by downloading the `Linux_2k.log` dataset. This file is great because it simulates a real-world Linux environment, filled with user sessions, system events, and—most importantly—authentication attempts.

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/0b0e2bffc6d9383b4f85c56dbf22969d9de39548/images/1.png)


### Step 2: First Look & Review
I opened the file in **VS Code** to keep things organized. To keep the analysis focused and high-quality, I decided to focus on the first **20 to 40 lines**. This helped me get familiar with the log structure without getting overwhelmed by thousands of lines of data.


![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/0b0e2bffc6d9383b4f85c56dbf22969d9de39548/images/2.png)

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/0b0e2bffc6d9383b4f85c56dbf22969d9de39548/images/2-1.png)

### Step 3: Hunting for Red Flags

I carefully scanned the entries looking for "red flags" that suggest a system is under attack. I specifically looked for:
* **Failed logins** coming repeatedly from the same IP address.
* Attempts to log in using **invalid or unknown usernames**.
* **Abnormal system exits** or alerts.

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/0b0e2bffc6d9383b4f85c56dbf22969d9de39548/images/2-3.png)


**Why does this matter?** These patterns usually mean someone (or a bot) is trying to brute-force their way into the system or looking for non-existent users to exploit.

### Step 4: Documentation
I made it a goal to log between **10 and 20 specific entries** from my initial sample. By focusing on this smaller set, I was able to practice a real SOC workflow (**Monitor → Detect → Analyze**) while ensuring I truly understood what each line of the log was telling me.

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/f93d3cce5b8b87f076ce9def48c0d3ce18d4f965/images/4.png)


Step 5: Summarize the Findings

Always write a summary :

The logs indicate several failed login attempts from the IP addresses 218.188.2.4 and
220.135.151.1, mainly targeting the root account. This strongly suggests the possibility
of brute-force attack attempts. The repeated failures from these specific IP addresses
indicate either automated attacks or probing activities. Additionally, the presence of
"user unknown" messages shows that attackers are randomly trying various usernames.
Moreover, the event labeled "ALERT exited abnormally" suggests there may be an
underlying system issue that requires further investigation.


# Project 2: Automating Log Analysis with Python

## About this Project
After getting my hands dirty with manual log review in Project 1, I realized that analyzing thousands of lines by hand isn't scalable. In this second phase, I took it a step further by **automating the process**. 

I wrote a Python script to scan through log files and instantly flag suspicious patterns. To simulate a more realistic scenario, I shifted my focus to a larger chunk of data (lines 200–500), showing how coding can make a SOC Analyst's job much more efficient.

## 🛠️ What I used
* **Language:** Python 3.x
* **Editor:** VS Code
* **Dataset:** The same `Linux_2k.log` from LogHub used in the beginner project.
* **Key Skills:** Scripting, pattern matching, and handling larger datasets.

---

##  The Automation Process

### Step 1: Setting up the Environment
I organized my workspace in **VS Code** by creating a dedicated project folder and a script named `log_analysis.py`. Keeping the log file and the script in the same directory made the execution seamless.

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/49325c1f4b1d36fb5cbff2a40dd22beea83547cd/images/2-1.png)


### Step 2: Developing the Script

The script was designed to perform four main tasks:

Python script for log_analysis.py:

 ![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/e21c5d22882a8a3ada789ae0ba7e6e938e032d19/images/script%201.png)
 ![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/e21c5d22882a8a3ada789ae0ba7e6e938e032d19/images/script%202.png)
 

1.  **Read the Data:** Open the `Linux_2k.log` file securely using Python.
2.  **Targeted Scanning:** Instead of looking at a few lines, I programmed it to slice the data and focus specifically on **lines 200 to 500**.
3.  **Pattern Detection:** I defined specific "red flags" for the script to hunt for, such as:
   
    * `Failed password`
    * `authentication failure`
    * `invalid user` or `user unknown`
     
5.  **Reporting:** The script categorizes each finding and prints a summary with the total count of suspicious events.

   ![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/49325c1f4b1d36fb5cbff2a40dd22beea83547cd/images/2-2.png)

   

### Step 3: Running the Analysis

By running `python log_analysis.py` in the terminal, the script instantly parsed the 300-line subset. 

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/49325c1f4b1d36fb5cbff2a40dd22beea83547cd/images/2-3.png)


It automatically flagged every instance of unauthorized access attempts, including the specific type of failure and the original log entry.


![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/49325c1f4b1d36fb5cbff2a40dd22beea83547cd/images/2-3-1.png)


### Step 4: Exporting Results for Professional Review

To wrap up the automation, I added a final step to the script that exports all flagged activity into a **CSV file** (`suspicious_logs.csv`)

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/582743655f9a22f7f2189937833145eef0dc50df/images/step%204%201.png)



Scanning logs in the terminal is great, but having them in a structured format like a spreadsheet is what makes the data actually actionable. I used Python's `csv` module to:

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/582743655f9a22f7f2189937833145eef0dc50df/images/step%204.png)

1. **Create a Header:** Organising the data into "Type" and "Log Entry" columns.
2. **Automate the Save:** The script now writes every finding into the file automatically.

### Structured Output Example
Once the script runs, the output in Excel or Google Sheets looks like this:

| Type | Log Entry |
| :--- | :--- |
| **Auth Failure** | Jun 22 03:17:26 combo sshd(pam_unix)[16206]: authentication failure; rhost=n219076184117... |
| **Auth Failure** | Jun 22 03:17:35 combo sshd(pam_unix)[16210]: authentication failure; rhost=n219076184117... |
| **Auth Failure** | Jun 22 03:17:36 combo sshd(pam_unix)[16212]: authentication failure; rhost=n219076184117... |

---

## 💡 Final Takeaway (Objective 2)
By completing this objective, I moved from manual observation to a **professional SOC workflow**. This automation allows me to handle much larger datasets (lines 200–500 and beyond) in a fraction of the time, providing a clean, structured report ready for further investigation or incident response documentation.




---














---

## 💡 Key Takeaway
This exercise taught me that security isn't just about automated tools; it's about knowing what "normal" looks like so you can spot the "suspicious."
