# CentOS 7 EOL Repository Fix
CentOS 7 OS repo problem and yum update error solved | رفع مشکل آپدیت در سنت 7


### Method 1: Automatically Replace the Repository File

#### Step 1: Backup Existing Repo Files

1. **Backup Existing Repo Files:**

   ```bash
   sudo cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
   ```

#### Step 2: Download the Updated Repository File

2. **Download the Updated Repository File:**

   ```bash
   # use curl (Only Iran)
   sudo curl -fsSL https://raw.githubusercontent.com/arminkit/centos7-repo/iran/CentOS-Base.repo -o /etc/yum.repos.d/CentOS-Base.repo
   # use curl
   sudo curl -fsSL https://raw.githubusercontent.com/arminkit/centos7-repo/other/CentOS-Base.repo -o /etc/yum.repos.d/CentOS-Base.repo
   # or use wget (Only Iran)
   # sudo wget -O /etc/yum.repos.d/CentOS-Base.repo https://raw.githubusercontent.com/arminkit/centos7-repo/iran/CentOS-Base.repo
   # or use wget
   # sudo wget -O /etc/yum.repos.d/CentOS-Base.repo https://raw.githubusercontent.com/arminkit/centos7-repo/other/CentOS-Base.repo
   ```

#### Step 3: Clean YUM Cache

3. **Clean YUM Cache:**

   Clear the YUM cache to ensure it fetches the latest repository metadata:

   ```bash
   sudo yum clean all
   sudo yum makecache
   ```

#### Step 4: Update Your System

4. **Update Your System:**

   Now try updating your system:

   ```bash
   sudo yum update
   ```

### Method 2: Manually Edit the Repository File

#### Step 1: Backup Existing Repo Files

1. **Backup Existing Repo Files:**

   ```bash
   sudo cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
   ```

#### Step 2: Edit the Repository File

2. **Edit the Repository File:**

   Open the repository file with a text editor:

   ```bash
   sudo nano /etc/yum.repos.d/CentOS-Base.repo
   ```

#### Step 3: Update the `baseurl`

3. **Update the `baseurl`:**

   Replace the `baseurl` entries with the following vault URLs: (Only Iran)

   ```ini
   [base]
name=ITO-Repo CentOS-$releasever - Base
baseurl=https://repo.ito.gov.ir/centos/7/os/$basearch/
gpgcheck=0
enabled=1
#released updates
[updates]
name=ITO-Repo CentOS-$releasever - Updates
baseurl=https://repo.ito.gov.ir/centos/$releasever/updates/$basearch/
gpgcheck=0
enabled=1
   ```

  Replace the `baseurl` entries with the following vault URLs:

   ```ini
   [base]
name=CentOS-$releasever - Base
baseurl=https://mirror.one3erver.com/centos/7.9.2009/os/x86_64/
enabled=1
gpgcheck=1
gpgkey=https://mirror.one3erver.com/centos/7.9.2009/os/x86_64/RPM-GPG-KEY-CentOS-7
 
[updates]
name=CentOS-$releasever - Updates
baseurl=https://mirror.one3erver.com/centos/7.9.2009/updates/x86_64/
enabled=1
gpgcheck=1
gpgkey=https://mirror.one3erver.com/centos/7.9.2009/os/x86_64/RPM-GPG-KEY-CentOS-7
   ```

   Save the file and exit the editor.

#### Step 4: Clean YUM Cache

4. **Clean YUM Cache:**

   Clear the YUM cache to ensure it fetches the latest repository metadata:

   ```bash
   sudo yum clean all
   sudo yum makecache
   ```

#### Step 5: Update Your System

5. **Update Your System:**

   Now try updating your system:

   ```bash
   sudo yum update
   ```

