# Phishing-Emails
The corporate EDR intercepted the following email and flagged it as a suspicious phishing email - Task scheduler requiring further investigation.

* EventID :82
* Event Time :Mar, 21, 2021, 12:26 PM
* Rule :Phishing Mail Detected - Suspicious Task Scheduler
* SMTP Address :189.162.189.159
* Source Address :aaronluo@cmail.carleton.ca
* Destination Address :mark@letsdefend.io
* E-mail Subject :COVID19 Vaccine
* Device Action :Blocked

# Investigation Steps

<h2>Gathering more info about the email</h2>

* Sender details:  aaronluo@cmail.carleton.ca
* Recipient details : mark@letsdefend.io
* The subject of the email: COVID19 Vaccine
* SMTP IP address : 189.162.189.159
* Attachment name: material.pdf
* Attachment MD5 checksum: :72c812cf21909a48eb9cceb9e04b865d
* Email body URL: no URL found in email body
* Date: Mar, 21, 2021, 12:26 PM

<h2>Checking the email attachment in the sandbox  environment</h2>

* The hybrid-analysis sandbox has been used for this investigation. 
* The attachment has been flagged as <strong>Malicious  - Trojan.PDF.Fraud </strong>
* 23 out of 62 Antivirus engines marked sample as malicious.

![image](https://github.com/user-attachments/assets/7e97c297-4d61-4305-921f-d68c49acd800)

* It is mapped to 4 MITREATT&CK Techniques shown below

![image](https://github.com/user-attachments/assets/05396dcb-365a-4594-aba6-11a1d5df53a2)

![image](https://github.com/user-attachments/assets/5bb25410-0481-4a15-81e8-2b3943454f1b)

* PDF file contains an embedded URL
  
![image](https://github.com/user-attachments/assets/e4fcde4c-7d9d-4258-a55b-9ed44bf5d341)

<strong>Checking  the SMTP IP address reputation on 'Abuseipdb' </strong>

* SMTP server  IP has been reported 207 originating from Mexico
* Associated with Brute Force and Port scan attacks

![image](https://github.com/user-attachments/assets/b66c7356-09e4-46c7-953b-61c8a40cdad3)



* It uses  AcroRd32.exe process
![image](https://github.com/user-attachments/assets/c2b7f481-1728-46b7-b514-19f9413329c1)


<strong>Checking  the EDR  for any C2 communication and data exfiltration  on Mark's PC </strong>

* Processes analysis: No suspicious process - AcroRd32.exe with PID7412 was found

* Network analysis: No relevant HTTP requests were made

* DNS requests: No relevant DNS requests were made

<strong> Verdict: The  PDF file was not opened. Hence, no data exfiltration had occurred </strong>


