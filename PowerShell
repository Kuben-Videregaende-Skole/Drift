
**Let's map out a curriculum that'll make this journey both educational and exciting:**

---

### **1. Introduction to PowerShell**

* **Goals:**
  - Familiarize students with the PowerShell environment.
  - Understand cmdlets, parameters, and object-oriented scripting.
  - Execute basic commands and navigate the file system.

* **Activities:**
  - **Exploring the Console:**
    - Open PowerShell as Administrator.
    - Use `Get-Command` to see available cmdlets.
  - **Basic Cmdlets:**
    - `Get-Help`, `Get-Service`, `Get-Process`, `Stop-Process`.

---

### **2. Configuring Network Settings**

* **Goals:**
  - Configure IP addresses, DNS servers, and default gateways using PowerShell.
  - Understand network adapters and their properties.

* **Key Commands:**

  ```powershell
  # View network adapters
  Get-NetAdapter

  # Set a static IP address
  New-NetIPAddress -InterfaceAlias "Ethernet0" -IPAddress "192.168.1.10" -PrefixLength 24 -DefaultGateway "192.168.1.1"

  # Set DNS server addresses
  Set-DnsClientServerAddress -InterfaceAlias "Ethernet0" -ServerAddresses "8.8.8.8","8.8.4.4"
  ```

* **Activity:**
  - Have students configure their server's network settings to communicate within a local network.

---

### **3. Renaming the Server**

* **Goals:**
  - Change the server's hostname using PowerShell.
  - Understand the impact of server names in a networked environment.

* **Key Command:**

  ```powershell
  # Rename the computer
  Rename-Computer -NewName "Server01" -Restart
  ```

* **Activity:**
  - Students choose meaningful names for their servers and rename them.

---

### **4. Installing Server Roles and Features**

* **Goals:**
  - Install roles like Active Directory Domain Services (AD DS), DNS, and DHCP via PowerShell.
  - Understand what roles and features are and their importance.

* **Key Command:**

  ```powershell
  # Install roles and features
  Install-WindowsFeature AD-Domain-Services,DNS,DHCP -IncludeManagementTools
  ```

* **Activity:**
  - Discuss the function of each role and have students install them.

---

### **5. Promoting to a Domain Controller**

* **Goals:**
  - Promote the server to a Domain Controller (DC).
  - Understand domains, forests, and the role of a DC.

* **Key Command:**

  ```powershell
  # Promote server to Domain Controller
  Install-ADDSForest -DomainName "example.local" -DomainNetbiosName "EXAMPLE" -SafeModeAdministratorPassword (ConvertTo-SecureString -AsPlainText "YourPassword1!" -Force) -InstallDns
  ```

* **Activity:**
  - Students set up their own domain.

* **Important Note:**
  - Emphasize the need for a strong DSRM (Directory Services Restore Mode) password.

---

### **6. Setting Up Organizational Units (OUs)**

* **Goals:**
  - Create OUs to organize users, groups, and computers.
  - Understand the hierarchical structure of AD.

* **Key Command:**

  ```powershell
  # Create an OU
  New-ADOrganizationalUnit -Name "Students" -Path "DC=example,DC=local"
  ```

* **Activity:**
  - Students design an OU structure for a hypothetical organization.

---

### **7. Adding Users and Groups**

* **Goals:**
  - Create users and groups within AD using PowerShell.
  - Set properties like passwords, account options, and group memberships.

* **Key Commands:**

  ```powershell
  # Create a new user
  New-ADUser -Name "John Doe" -SamAccountName "jdoe" -UserPrincipalName "jdoe@example.local" -Path "OU=Students,DC=example,DC=local" -AccountPassword (ConvertTo-SecureString -AsPlainText "Password123!" -Force) -Enabled $true

  # Create a new group
  New-ADGroup -Name "IT Staff" -GroupScope Global -Path "OU=Staff,DC=example,DC=local"

  # Add user to group
  Add-ADGroupMember -Identity "IT Staff" -Members "jdoe"
  ```

* **Activity:**
  - Import users from a CSV file and create bulk user accounts.

---

### **8. Implementing Group Policies**

* **Goals:**
  - Create and link Group Policy Objects (GPOs) to OUs.
  - Enforce policies across users and computers.

* **Key Commands:**

  ```powershell
  # Create a new GPO
  New-GPO -Name "Student Restrictions" -Comment "GPO for student accounts"

  # Link GPO to OU
  New-GPLink -Name "Student Restrictions" -Target "OU=Students,DC=example,DC=local"

  # Set a policy (e.g., disable command prompt)
  Set-GPRegistryValue -Name "Student Restrictions" -Key "HKCU\Software\Policies\Microsoft\Windows\System" -ValueName "DisableCMD" -Type DWord -Value 1
  ```

* **Activity:**
  - Students create a policy that restricts certain applications or settings.

---

### **9. Configuring DHCP**

* **Goals:**
  - Set up DHCP scopes and options.
  - Understand IP address allocation.

* **Key Commands:**

  ```powershell
  # Add DHCP scope
  Add-DhcpServerv4Scope -Name "Main Scope" -StartRange 192.168.1.100 -EndRange 192.168.1.200 -SubnetMask 255.255.255.0

  # Set DNS server options for DHCP clients
  Set-DhcpServerv4OptionValue -OptionId 6 -Value "192.168.1.10" -ScopeId 192.168.1.0
  ```

* **Activity:**
  - Students configure scopes and test IP address leasing.

---

### **10. Advanced Automation and Scripting**

* **Goals:**
  - Write scripts to automate repetitive tasks.
  - Introduce error handling and logging.

* **Key Concepts:**

  - **ForEach Loops:**
    ```powershell
    $users = Import-Csv -Path "C:\Users.csv"
    foreach ($user in $users) {
        # Create user accounts
    }
    ```

  - **Error Handling:**
    ```powershell
    Try {
        # Command that might fail
    } Catch {
        # Handle the error
    }
    ```

* **Activity:**
  - Automate the creation of users and groups.
  - Implement logging to track script execution.

---

### **Visual Learning with Flowcharts**

**Overall Process Flow:**

```
[Start]
   |
   v
[Introduction to PowerShell]
   |
   v
[Configure Network Settings]
   |
   v
[Rename Server]
   |
   v
[Install Roles]
   |
   v
[Promote to Domain Controller]
   |
   v
[Set Up OUs]
   |
   v
[Add Users and Groups]
   |
   v
[Implement Group Policies]
   |
   v
[Advanced Automation]
   |
   v
[End]
```

---

### **Extra Tips to Enhance the Experience**

- **Interactive Labs:** Set up virtual environments where students can practice without fear of breaking anything critical.
- **Real-World Scenarios:** Pose challenges like simulating password expirations or creating custom policies for different departments.
- **Peer Collaboration:** Encourage students to work in pairs or small groups to foster teamwork.

---

### **Beyond the Basics**

**1. Introducing PowerShell Functions and Modules**

* Teach students how to create reusable code with functions.
* Package functions into modules for easier distribution.

**2. Version Control with Git**

* Introduce Git for managing script versions.
* Host a simple repository on GitHub or a local server.

**3. Exploring PowerShell Remoting**

* Enable students to manage remote servers.
* Use `Enter-PSSession` and `Invoke-Command` for remote management.

---

### **Resources They'll Love**

- **Microsoft Learn:**
  - [PowerShell Documentation](https://docs.microsoft.com/en-us/powershell/)
  - [Windows Server Documentation](https://docs.microsoft.com/en-us/windows-server/)

- **Community Blogs and Tutorials:**
  - [PowerShell.org](https://powershell.org/)
  - [Adam the Automator Blog](https://adamtheautomator.com/)

- **YouTube Channels:**
  - **TechThoughts**
  - **The Blind Coder**

---

### **Spark Their Curiosity**

Consider wrapping up the course with a capstone project:

- **Project Idea:** Each student sets up a mini enterprise network environment, automating as much as possible. They can present their environment, explain the choices they made, and demo automated tasks.

---
