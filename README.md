# Automated Job Application Tracker Using Power Automate

## 1. Introduction: The Job Application Challenge

For many recent graduates and job seekers, applying for jobs is a time-consuming and often overwhelming process. With hundreds of applications sent out over a short period, it becomes difficult to track which positions have been applied for, the responses received, and the necessary follow-ups required.

### 1.1 The Need for a Job Application Tracker

Without a structured tracking system, job seekers face several challenges:

- **Missed follow-ups:** Many candidates forget to follow up with recruiters, reducing their chances of securing an interview.
- **Lack of visibility into application status:** Checking emails manually for updates such as "Application Viewed" or "Unfortunately, we have decided to move forward with another candidate" is inefficient.
- **No centralized dashboard:** There is no single platform that consolidates all application-related information, such as the number of applications sent, the number of rejections received, and pending responses.

A well-designed automation system can solve these problems by automatically tracking applications, updating statuses, and scheduling follow-ups without requiring manual intervention.

## 2. Existing Solutions and Why This Automation Was Developed

### 2.1 Alternative Online Job Tracking Tools

There are several existing tools that assist with job tracking, but they have key limitations:

| Tool                                    | Limitations                                                                                              |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Google Sheets                           | Requires manual entry for each application.                                                              |
| Job Search Platforms (LinkedIn, Indeed) | Tracks only applications submitted through their platform and does not consolidate all job applications. |
| Dedicated Job Tracking Apps             | Often require a paid subscription and lack full automation.                                              |
| Trello/Notion                           | Requires manual updates and does not automate follow-ups or job status updates.                          |

### 2.2 Why This Automation Was Developed

Existing tools lack complete automation, email integration, and structured follow-up reminders. This Power Automate-based solution addresses these gaps by:

- Automatically extracting job application data from emails.
- Tracking application statuses in a structured format.
- Automating follow-up reminders without manual input.

This system integrates Power Automate, Gmail API, and Excel automation to create an end-to-end job tracking system that operates seamlessly and reduces the time spent manually updating job applications.

## 3. Why Power Automate?

Power Automate was chosen because it:

- Enables automation between multiple services, including Gmail, Excel, and Notifications.
- Provides workflow management with conditional logic to determine the next steps based on the email content.
- Supports API integration, allowing for the use of a custom Gmail connector.
- Allows for low-code/no-code automation but can be extended with advanced configurations if needed.

The plan for this automation involved:

1. Extracting job application updates from LinkedIn emails.
2. Processing the extracted data and storing it in an Excel file.
3. Automatically updating application statuses based on email content.
4. Sending reminders for follow-ups at scheduled intervals.
5. Overcoming Gmail & Power Automate security restrictions using a custom connector.

## 4. Detailed Explanation of the Process

The automation consists of three major components:

- Email Processing and Data Extraction
- Decision Logic for Classification
- Updating and Tracking Applications in Excel

### 4.1 Flowchart of the Automation Process

The diagram below represents the automation process in Power Automate.

- **Trigger:** The process starts when an email from LinkedIn is received.
- **Data Extraction:** The email content is converted from HTML to text, and key details such as the Company Name, Job Title, Date, and Status are extracted.
- **Decision Point:** The system determines whether the email confirms an application submission or provides an update on the application status.
- **Data Storage & Updates:** If it is a new application, a new row is added to the tracking sheet; if it is an update (e.g., "Application Viewed"), the existing entry is modified.
- **Scheduled Follow-Ups:** The system checks applications at defined intervals and sends reminders accordingly.

### 4.2 Step 1: Email Processing & Data Extraction

#### Trigger:

- The process is initiated when Gmail receives a job application-related email from LinkedIn.

#### Actions Taken:

1. Convert the email from HTML to text to make the content readable.
2. Extract the following information:
   - Company Name
   - Position Applied For
   - Date Received
   - Application Status (e.g., "Applied," "Viewed," "Rejected")

#### Challenges Faced:

- Gmail’s security policies prevent Power Automate from directly retrieving email data due to restricted API access.
- Microsoft Outlook has built-in Power Automate connectors, but Gmail requires additional authentication steps.

#### Solution Implemented:

- A Custom Gmail Connector was developed using Google Cloud Platform (GCP) OAuth 2.0 authentication.
- This connector allows Power Automate to securely access emails, extract the required data, and process it for tracking.

### 4.3 Step 2: Decision Logic – Classifying Email Type

- If the email contains the phrase "Your application was sent to [Company Name]", it is classified as a new application entry (Flow 1).
- If the email contains the phrase "Viewed" or "Unfortunately", it is classified as an application status update (Flow 2).

### 4.4 Step 3: Flow 1 – Adding a New Job Entry to Excel

- If an application is detected as new, the system inserts a new row into the job tracking Excel sheet.
- The row includes:
  - Company Name
  - Position Applied For
  - Date Applied
  - Status: "Applied"

### 4.5 Step 4: Flow 2 – Updating Job Application Status

- If an email indicates an application status update, the system first searches the Excel sheet for the existing entry.
- If the Company Name and Position exist, the Status column is updated accordingly.
- If no existing entry is found, a new row is added with full details.

### 4.6 Step 5: Follow-Up Reminder Automation

#### Trigger:

- The follow-up system runs twice daily (9 AM and 2 PM).

#### Logic and Actions:

- The automation scans the Excel sheet for applications that were submitted 3 and 7 days ago.
- If an application has not received any response, a reminder notification is sent suggesting a follow-up.
- If an application has already been marked as Viewed or Rejected, no reminder is sent.

## 5. Conclusion and Future Improvements

This automation project successfully:

- Eliminates manual effort in job application tracking.
- Ensures real-time status updates without needing to check emails manually.
- Improves follow-up efficiency to increase response rates from recruiters.

## Final Thoughts and Next Steps

Through this project, I successfully implemented job application tracking automation using Power Automate, overcoming key challenges such as API restrictions, authentication barriers, regional failures, and HTML data extraction. This experience not only strengthened my understanding of workflow automation but also provided valuable insights into troubleshooting and optimizing real-world automation processes.

Now, it's time to take this knowledge further—applying the same problem-solving mindset to AI-driven automation and intelligent agent technology. As I explore AI agents and their potential in automation, I look forward to developing more advanced, intelligent systems that push the boundaries of efficiency and innovation.

**- Santhosh Botcha**

