# Week-03-JTR-Password-Cracking-Networkwalks
Week 3 cybersecurity internship project focused on password cracking with John the Ripper (JTR) using Kali Linux, including PDF hash extraction, password recovery, and flag capture.
# Week 3 – Password Cracking with John the Ripper (JTR)

## Internship
**Networkwalks – Cybersecurity Internship**


## Project Overview

In Week 3, I worked on a practical password-cracking lab using **John the Ripper (JTR)**.

The objective was to recover the passwords of three protected PDF files provided for the lab and use the recovered passwords to open the files.

---

## Tools Used

- Kali Linux
- John the Ripper (JTR)
- `pdf2john.pl`
- RockYou wordlist
- Terminal

---

## Steps Performed

### 1. Prepared the Protected PDF Files

I worked with three password-protected PDF files provided as part of the Networkwalks lab:

- My Locked PDF 1
- My Locked PDF 2
- My Locked PDF 3

---

### 2. Extracted the PDF Hash

I used the `pdf2john.pl` utility included with John the Ripper to extract the password hash from each protected PDF.

Example:

```bash
/usr/share/john/pdf2john.pl "My Locked PDF1.pdf" > hash1.txt

3. Prepared the Hash<img width="934" height="624" alt="PDF3 Password" src="https://github.com/user-attachments/assets/5352a062-8388-4952-8c44-ba76c8edd1cc" />
<img width="934" height="617" alt="PDF2 Password" src="https://github.com/user-attachments/assets/482428ad-b192-4ae6-8d62-b52882a6eeb4" />
<img width="931" height="765" alt="PDF1 Password" src="https://github.com/user-attachments/assets/ea0618f0-e1fb-413c-a04b-61f43b3fceab" />


The extracted file contained the PDF filename along with the hash.

I created a clean hash file using:

cut -d ':' -f2- hash1.txt > pdfhash.txt

The same process was followed for the other PDF files.

4. Password Recovery Using John the Ripper

I used John the Ripper with the RockYou wordlist to perform the password recovery:

john --format=pdf --wordlist=/usr/share/wordlists/rockyou.txt pdfhash.txt

John tested passwords from the wordlist against the extracted PDF hash.

5. Verified the Recovered Password

I used the following command to display the recovered password:

john --show --format=pdf pdfhash.txt

The same verification process was performed for all three PDFs.

6. Opened the Protected PDFs

After recovering the passwords, I used them to successfully open the three protected PDF files.

Results

All three protected PDFs were successfully processed and their corresponding flags were captured.

PDF	Result
PDF 1	Password recovered and flag captured
PDF 2	Password recovered and flag captured
PDF 3	Password recovered and flag captured

Captured Flags
PDF 1: nw{cybersecurity_flag_captured_2608}
PDF 2: nw{networkwalks_persistence_jtr_270521}
PDF 3: nw{networkwalks_flag_260821_1}

Key Learning

Through this project, I gained practical experience in:

Extracting password hashes from protected PDF files
Understanding PDF password hashes
Using pdf2john.pl
Using John the Ripper
Working with password wordlists
Verifying recovered passwords
Understanding the importance of strong passwords
