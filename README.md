# Linux Mail Server Project (Postfix)

**Author:** Lindsey Udeh
**Date:** October 2025
**Platform:** Ubuntu Server 24.04 LTS (on VirtualBox)
**Type:** Home Lab / Practical System Administration Project

---

## Overview
## Steps Completed
## Tools Used
## Learning Outcomes
## Next Steps

---

## Overview
This project demonstrates how to **install, configure, and test a local mail server** using **Postfix** on a Linux virtual machine.
It simulates how real system administrators handle user mail delivery, permissions, and troubleshooting.

---

#Steps Completed

# 1 Install Postfix and Mail Utilities
```bash
sudo apt update
sudo apt install postfix mailutils -y
```

# 2 Create Local Users
```bash
sudo adduser sysadmin
sudo adduser testuser
```

# 3 Configure Virtual Address Mapping
Edited /etc/postfix/virtual and add: 
admin@lindsey-lab     sysadmin
support@lindsey-lab   testuser
testuser@lindsey-lab  testuser

Then applied changes:
```bash
sudo postmap /etc/postifx/virtual
```

# 4 Restart and Enable Postfix
```bash
sudo systemctl restart postfix
sudo systemctl enable postfix
```

# 5 Create Mail Directory and Set Permissions
```bash
sudo mkdir -p /var/mail/testuser
sudo chown testuser:mail /var/mail/testuser
sudo chmod 660 /var/mail/testuser
```

# 6 Send and Verify Emails
```bash
echo "hi local" | mail -s "local-only" testuser
echo "hi domain" | mail -s "host-domain" testuser@lindsey-lab
mail
```

# Screenshots
![Mail Server Running](https://github.com/user-attachments/assets/fce90b9a-07bd-4ba0-a623-ab901de35e94)

# Tools Used
- Ubuntu Server 24.04 LTS (VirtualBox VM)
- Postfix (MTA)
- Mailutils (Command line mail tool)
- Bash shell

## Learning Outcomes
- Installed and configured a Mail Transfer Agent (Postfix)
- Managed user accounts and mail permissions
- Verified mail delivery and troubleshooting logs
- Practiced real-world system administrators workflow

## Next Steps
- Add Dovecot for IMAP/POP3 access
- Implement spam filter integration (SpamAssassin)
- Configure mail relay for external delivery

# Result
A fully functional local maiil server running on Ubuntu, capable of sending and receiving interal messages between system users
>>>>>>> bde283fe32616ad19c8bd57b5dbdb746e5454202
