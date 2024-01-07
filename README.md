# Threat-Intelligence-in-Microsoft-sentinel
KQL for Threat Hunt, Different attacks, Automations 

Hunting with KQL

-failed login attemps from a specific IP address
securityEvent
|where EventID == 4626//4626 represents failed login attemp event
|where IPAddress =="x.x.x.x"// Replace x.x.x.x with the specific IP addres
|where TimeGenerated, Account, IPAddress, computer

NOTE:This query will search the SecurityEvent table for event ID 4625 (failed login attempts) and filter the results to display entries where the IP address matches the specified value. Adjust the columns in the project statement as per your requirement.
Remember, KQL queries in Microsoft Sentinel allow you to analyze and manipulate data effectively. You can filter, project, join, summarize, and perform various operations on data using KQL syntax.
Feel free to modify this query based on your specific use case or data schema in Sentinel.


Alert you when an anomalous number of resources is created in AZURE Activity
| where OperationNameValue == "MICROSOFT.COMPUTER/VIRTUALMACHINE/WRITE" or OperationNameValue == "MICROSOFT RESOURCES/DEPLOYEMENTS/WRITE"
|where ActivityStatusValue == " Succeedded"
|make-series dcount(ResourceId) default=0 on EventSubmissionTimestamp in range(ago(7d),now(),1d)by caller

Here are Attack and their explanations
Identity-Based Attacks:Identity-based attacks focus on exploiting vulnerabilities related to user identities, credentials, or personal information. These attacks aim to compromise, steal, or misuse sensitive data, often for financial gain or unauthorized access. Some common types of identity-based attacks include:

Phishing: Deceptive attempts to acquire sensitive information by posing as a trustworthy entity.

Credential Stuffing: Using stolen credentials (username/password) to gain unauthorized access by trying them across multiple sites or services.

Identity Theft: Stealing personal information to impersonate an individual for financial gain or fraudulent activities.

Man-in-the-Middle (MITM) Attacks: Intercepting communication between parties to eavesdrop, alter, or steal sensitive information.

Brute Force Attacks: Repeatedly trying various combinations of credentials to gain access to a system or an account.

Honeytokens: Honeytokens are pieces of fake or decoy data placed within a system to detect unauthorized access or monitor potential security breaches. They resemble real data but are not used in legitimate operations. Honeytokens are strategically placed within a network, database, or system to attract attackers. If accessed or triggered, they signal a security breach, helping security teams identify and respond to potential threats. Honeytokens can be in the form of unused credentials, fake files, or false database entries.

Sensitive Tags: Sensitive tags or sensitive data labels are applied to specific information within a system or database that requires special protection due to its confidentiality, privacy, or regulatory compliance. These tags help identify and categorize sensitive information, such as personally identifiable information (PII), financial records, health data, intellectual property, etc. By labeling data with sensitive tags, organizations can implement strict access controls, encryption, and other security measures to prevent unauthorized access or leakage of sensitive information.
Understanding these concepts is crucial for maintaining robust cybersecurity practices, safeguarding sensitive data, and detecting potential security threats within an organization's systems and networks.![image]

       Daily Automation Task
 Threat Hunting: Automate the process of searching for potential threats and anomalies within the collected data using predefined queries or custom hunting queries.
 
 Alert Prioritization and Triage: Automatically prioritize and triage alerts based on severity, potential impact, or relevance. This can involve categorizing alerts and assigning them to appropriate teams or workflows.

Automated Remediation: Implement automated response actions to address security threats or incidents. For instance, automatically blocking a malicious IP address or isolating a compromised system.![image]

Fallow me for more tips ....    WORK FAST AND SMART




  
