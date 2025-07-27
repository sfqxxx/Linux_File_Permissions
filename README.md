# Linux_File_Permissions
This tutorial explains you the limux file permission in detail.
# Essential chmod Commands Tutorial

## What is chmod?

`chmod` (change mode) is used to change file and directory permissions in Linux.

## Permission Numbers

Each permission has a numeric value:
- **Read (r) = 4**
- **Write (w) = 2** 
- **Execute (x) = 1**

Add them together for each user group (Owner, Group, Others).
---
## Most Common chmod Commands

### chmod 777 - Full Permissions for Everyone
```bash
chmod 777 filename
```
- **What it means:** `rwxrwxrwx` - Everyone can read, write, and execute
- **When to use:** Almost never! Major security risk
- **Why dangerous:** Anyone can modify or delete your files

### chmod 755 - Standard Directory/Script Permissions
```bash
chmod 755 script.sh
chmod 755 /path/to/directory
```
- **What it means:** `rwxr-xr-x` - Owner full access, others read+execute only
- **Best for:** Executable scripts, directories

### chmod 644 - Standard File Permissions
```bash
chmod 644 document.txt
```
- **What it means:** `rw-r--r--` - Owner can edit, others read-only
- **Best for:** Regular text files, documents

### chmod 600 - Private File
```bash
chmod 600 private.txt
```
- **What it means:** `rw-------` - Only owner can read/write
- **Best for:** Sensitive files, SSH keys

---

## Quick Examples

### Make Script Executable
```bash
# Create script
echo '#!/bin/bash\necho "Hello"' > test.sh

# Make executable
chmod 755 test.sh

# Run it
./test.sh
```

### Fix "Permission Denied" Error
```bash
# Can't run script? Add execute permission
chmod +x script.sh

# Can't edit file? Add write permission
chmod u+w filename
```

### Secure a File
```bash
# Make file private (only you can access)
chmod 600 sensitive_data.txt
```

---

## Symbolic Method (Alternative)

| Command | Same as | Meaning |
|---------|---------|---------|
| `chmod +x file` | `chmod 755 file` | Add execute permission |
| `chmod u+w file` | - | Add write permission for owner |
| `chmod go-rwx file` | `chmod 600 file` | Remove all permissions from group/others |

---

## ⚠️ Important Warnings

### Never Use These Commands:
```bash
# DON'T DO THIS - Security nightmare!
chmod 777 *
chmod -R 777 /

# These make everything writable by anyone
chmod 666 filename
```

### Safe Practice:
```bash
# Check permissions first
ls -l filename

# Use minimal permissions needed
chmod 644 regular_file.txt    # For documents
chmod 755 executable_script   # For scripts
chmod 600 private_file.txt    # For sensitive data
```

---

## Quick Reference

| Permission | Number | Use Case |
|------------|--------|----------|
| `777` | `rwxrwxrwx` | ❌ Don't use (security risk) |
| `755` | `rwxr-xr-x` | ✅ Scripts, directories |
| `644` | `rw-r--r--` | ✅ Regular files |
| `600` | `rw-------` | ✅ Private files |

---

## Common Commands
```bash
chmod 755 script.sh          # Make script executable
chmod 644 *.txt             # Set standard file permissions
chmod 600 ~/.ssh/id_rsa     # Secure SSH key
chmod u+x filename          # Add execute for owner only
ls -l                       # View current permissions
```

**Remember:** Use the least permissions necessary for security!
