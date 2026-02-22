
# `linux-notes.md`

````markdown
#  Linux Command Notes

This document contains basic Linux commands I learned and practiced during my cybersecurity foundation phase.

---

## 📂 1. File & Directory Commands

### ls
List files and directories.

```bash
ls
````

### ls -a

List all files including hidden files.

```bash
ls -a
```

### ls -l

List files with detailed information (permissions, owner, size).

```bash
ls -l
```

### pwd

Print current working directory.

```bash
pwd
```

### mkdir

Create a new directory.

```bash
mkdir folder_name
```

### cd

Change directory.

```bash
cd folder_name
```

### rm

Remove a file.

```bash
rm file.txt
```

### rm -r

Remove a directory and its contents.

```bash
rm -r folder_name
```

---

## 📄 2. Viewing & Editing Files

### cat

Display file contents.

```bash
cat file.txt
```

### head

Display first few lines of a file.

```bash
head -n 5 file.txt
```

### tail

Display last few lines of a file.

```bash
tail -n 5 file.txt
```

### nano

Open file in text editor.

```bash
nano file.txt
```

---

## 🔎 3. Searching & Filtering

### grep

Search for a word or pattern.

```bash
grep "word" file.txt
```

### find

Search for files in directories.

```bash
find /home -name file.txt
```

---

##  4. Pipes

Pipe ( | ) passes output of one command into another.

Example:

```bash
cat file.txt | grep "name"
```

This displays only lines containing "name".

---

##  5. Permissions

### chmod

Change file permissions.

```bash
chmod 755 file.txt
```

Permission meaning:

* r = read
* w = write
* x = execute

755 means:

* Owner → read, write, execute
* Group → read, execute
* Others → read, execute

### chown

Change file ownership.

```bash
chown user:user file.txt
```

---

##  6. Users & Processes

### whoami

Show current user.

```bash
whoami
```

### sudo

Run command as superuser.

```bash
sudo command
```

### ps aux

Show running processes.

```bash
ps aux
```

### top

Display real-time process usage.

```bash
top
```

---

##  7. Networking Basics

### ifconfig

Show network interface details.

```bash
ifconfig
```

### ping

Test connectivity to another host.

```bash
ping google.com
```

### netstat

Show active network connections.

```bash
netstat -tulnp
```

---

##  8. Package Management (Debian/Ubuntu)

### Update packages

```bash
sudo apt update
```

### Install package

```bash
sudo apt install nmap
```

---

##  9. Downloading Files

### wget

Download files from internet.

```bash
wget File name
```

---

##  Why Linux is Important in Cybersecurity

Most servers, cloud systems, and security tools run on Linux. Understanding file systems, permissions, processes, and networking is essential for penetration testing and defensive security roles.

