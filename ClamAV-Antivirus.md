

---

### **ClamAV Antivirus Installation, Configuration, and Scanning**

**ClamAV** is an open-source antivirus engine designed to detect trojans, viruses, malware, and other malicious threats. Below is a detailed guide for installing, configuring, and running ClamAV on your system.

---

### **Step 1: Repository Check**

Before installing **ClamAV**, ensure the required repositories are enabled.

1. **List all repositories**:
   ```bash
   yum repolist all
   ```

---

### **Step 2: Install ClamAV**

To install **ClamAV** and its related packages, use the following command:

1. **Install ClamAV**:
   ```bash
   sudo yum install clamav*
   ```

---

### **Step 3: Verify Installation**

After installation, verify that **ClamAV** is installed correctly.

1. **Check package information**:
   ```bash
   rpm -qi clamav
   ```

2. **List all files installed by the ClamAV package**:
   ```bash
   rpm -ql clamav
   ```

---

### **Step 4: Install FreshClam**

**FreshClam** is a utility used to update the ClamAV virus definition database. To install it:

1. **Install FreshClam**:
   ```bash
   sudo yum install clamav-freshclam
   ```

---

### **Step 5: Update Virus Database**

To keep your ClamAV virus definitions up-to-date, you must run **FreshClam**.

1. **Update the virus database**:
   ```bash
   sudo freshclam
   ```

---

### **Step 6: Running a Scan with ClamAV**

Now, you can use **ClamAV** to scan your system for potential threats.

1. **Basic scan** (scan the current directory):
   ```bash
   clamscan
   ```

2. **Scan a specific directory** (e.g., `/root`):
   ```bash
   clamscan /root/
   ```

3. **Recursive scan** (scan a directory and its subdirectories):
   ```bash
   clamscan -r /root/
   ```

4. **Scan a directory containing potential threats**:
   ```bash
   clamscan -r /root/webshells/
   ```

---

### **Step 7: Download Test Malware Files**

To validate **ClamAV**'s functionality, download **EICAR** test files, which are safe test files used by antivirus software to verify detection.

1. **Download EICAR test files**:
   ```bash
   wget --no-check-certificate https://secure.eicar.org/eicar.com
   wget --no-check-certificate https://secure.eicar.org/eicar.com.txt
   wget --no-check-certificate https://secure.eicar.org/eicar_com.zip
   ```

---

### **Step 8: Advanced Scanning Options**

1. **Recursive scan** of the root directory:
   ```bash
   clamscan -r /root/
   ```

2. **Scan recursively and display only infected files**:
   ```bash
   clamscan -ir /root/
   ```

3. **Scan and log infected files** (log to `/root/clamav.log`):
   ```bash
   clamscan -ir /root/ -l /root/clamav.log
   ```

4. **Scan and remove infected files**:
   ```bash
   clamscan --remove -ir /root/
   ```

5. **Remove infected files from a specific directory**:
   ```bash
   clamscan --remove -r /root/webshells/
   ```

---

### **Step 9: Review Logs**

After scanning, view the scan logs to check the results.

1. **View the scan log**:
   ```bash
   cat /root/clamav.log
   ```

---
