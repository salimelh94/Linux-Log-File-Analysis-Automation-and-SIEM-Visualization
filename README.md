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

##  Final Takeaway (Objective 2)
By completing this objective, I moved from manual observation to a **professional SOC workflow**. This automation allows me to handle much larger datasets (lines 200–500 and beyond) in a fraction of the time, providing a clean, structured report ready for further investigation or incident response documentation.


# Objective 3: Log Analysis and Visualization with Splunk

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/c229108c8653a09dbc739e3c56acb16343df9dbd/images/ciscosplunk.jpg)


##  Project Overview
Building on my previous manual and automated analysis, this stage introduces **Splunk**, a professional **SIEM (Security Information and Event Management)** tool used in real-world SOC environments. 

In this phase, I moved beyond simple scripts to learn how to ingest, query, and visualize log data at scale. This allows for a much more powerful way to identify suspicious activities across large datasets.

##  Prerequisites
* **Foundation:** Completed Objectives 1 and 2 (understanding log structures and threat indicators).
* **Environment:** Splunk Enterprise (Free Trial).
* **Dataset:** The `Linux_2k.log` file from LogHub.
* **Concepts:** Basic understanding of data searching and filtering within a SIEM.

---

##  Setup and Configuration

### Step 1: Installing Splunk Enterprise



To get started, I set up a professional monitoring environment:
* **Download:** I visited the [official Splunk website](https://www.splunk.com/en_us/download.html) and opted for the **Splunk Enterprise** free trial.

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/c229108c8653a09dbc739e3c56acb16343df9dbd/images/3-1.png)

  
* **Setup:** Since my current environment is running on **Windows**, I chose the corresponding installation package

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/098fac4b227ee75d1bfdef525cee3fb2a8c67f63/images/4-2.png)

  
* **Account Creation:** I registered my account and configured a local admin user with secure credentials to manage the instance.


### Step 2: Accessing the Dashboard

Once the installation was complete:
1. I launched Splunk, which redirected me to the web-based login interface.

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/c229108c8653a09dbc739e3c56acb16343df9dbd/images/3-2.png)

  
3. After authenticating with my admin credentials, I successfully accessed the **Administrator Dashboard**.

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/c229108c8653a09dbc739e3c56acb16343df9dbd/images/3-3.png)

   
5. This dashboard serves as my central hub for data ingestion and security monitoring.

---

##  What's Next?
With the SIEM environment now live, the next steps involve uploading the `Linux_2k.log` data to begin creating advanced queries and visual dashboards to track security threats in real-time.

---

### Step 2: Uploading the Log File


Once I had the dashboard ready, I moved on to ingesting the data. I went to **Settings → Add Data** and chose the **Upload** option to bring in the same `Linux_2k.log` file I used in the previous objectives.


![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/2bc49a7a4cda780141f3ddc68ce53c426eaed719/images/3-4.png)



After selecting the file, I moved to the **Source Type** section. Splunk is pretty smart and automatically detected the format, but to keep things organized, I clicked **Save As** and filled out the configuration like this:

![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/2bc49a7a4cda780141f3ddc68ce53c426eaed719/images/3-5.png)


![images alt](https://github.com/salimelh94/Linux-Log-File-Analysis-Automation-and-SIEM-Visualization/blob/2bc49a7a4cda780141f3ddc68ce53c426eaed719/images/3-6.png)



* **Source Type:** (Left as the default auto-detected value)
* **Name:** Linux
* **Description:** Log Analysis
* **Category:** Custom
* **App:** Search & Reporting
  

Moving into the **Input Settings**, I set the **Host** to a constant value (**LAPTOP-8LP9R63O**) and chose the **Default index**. Doing this ensures that all my log events are properly labeled and stored so I can find them easily later. *(Note: This host value was specific to my device and will vary depending on the machine being used).*

**A quick troubleshooting tip:** During the upload, I found that if Splunk throws an error like *"Upload failed with ERROR: can only concatenate str (not 'NoneType') to str,"* the best fix is to simply rename the log file to **"Linux2k"** and try again. Splunk can be a bit picky if the filename or path contains spaces or special characters!












---

## 💡 Key Takeaway
This exercise taught me that security isn't just about automated tools; it's about knowing what "normal" looks like so you can spot the "suspicious."
