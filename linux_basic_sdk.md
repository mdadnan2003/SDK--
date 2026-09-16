# 🐧 Linux Basic SDK

> Daily Linux commands and concepts — beginner to practical level.

---

# 📚 Table of Contents

1. Linux Kya Hai?
2. Terminal
3. Shell
4. File System
5. pwd
6. ls
7. cd
8. mkdir
9. touch
10. cat
11. less
12. head
13. tail
14. cp
15. mv
16. rm
17. rmdir
18. clear
19. man
20. help
21. File Paths
22. Absolute vs Relative Path
23. Hidden Files
24. Wildcards
25. grep
26. find
27. locate
28. wc
29. sort
30. uniq
31. cut
32. tee
33. Pipes
34. Redirection
35. Command Chaining
36. echo
37. Environment Variables
38. export
39. PATH
40. Users
41. Groups
42. sudo
43. File Permissions
44. chmod
45. chown
46. chgrp
47. Processes
48. ps
49. top
50. htop
51. kill
52. jobs
53. background/foreground
54. systemctl
55. journalctl
56. Disk Space
57. du
58. df
59. free
60. Networking Basics
61. ip
62. ping
63. curl
64. wget
65. ss
66. DNS
67. hostname
68. Package Management
69. APT
70. Pacman
71. Filesystem Mounting
72. Archive Files
73. tar
74. zip/unzip
75. SSH
76. SCP
77. rsync
78. Git
79. Python Environment
80. Node.js
81. Ports
82. Services
83. Cron
84. Logs
85. Aliases
86. Bash History
87. Bash Scripts
88. Variables in Scripts
89. Conditions
90. Loops
91. Functions
92. Troubleshooting
93. Important Directories
94. Linux Cheat Sheet
95. Daily Workflow

---

# 1. Linux Kya Hai?

Linux ek open-source operating system kernel hai.

Popular Linux distributions:

```text
Ubuntu
Debian
Fedora
Arch Linux
Linux Mint
Kali Linux
AlmaLinux
Rocky Linux
```

Simple architecture:

```text
Hardware
   ↓
Kernel
   ↓
Shell
   ↓
Commands / Applications
   ↓
User
```

---

# 2. Terminal

Terminal se hum commands ke through system ko control karte hain.

Example:

```bash
ls
```

```bash
pwd
```

```bash
cd Documents
```

---

# 3. Shell

Shell command ko interpret karta hai.

Common shells:

```text
bash
zsh
fish
```

Check current shell:

```bash
echo $SHELL
```

Check shell version:

```bash
bash --version
```

---

# 4. Linux File System

Linux mein everything is organized under:

```text
/
```

Example:

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── opt
├── proc
├── root
├── tmp
├── usr
└── var
```

---

# 5. pwd

Current directory:

```bash
pwd
```

Example:

```text
/home/adnan/projects
```

---

# 6. ls

Files/folders dekhne ke liye:

```bash
ls
```

Detailed:

```bash
ls -l
```

Hidden files:

```bash
ls -a
```

Detailed + hidden:

```bash
ls -la
```

Human-readable:

```bash
ls -lh
```

---

# 7. cd

Directory change:

```bash
cd Documents
```

Parent directory:

```bash
cd ..
```

Home:

```bash
cd ~
```

Root:

```bash
cd /
```

Previous directory:

```bash
cd -
```

---

# 8. mkdir

Directory create:

```bash
mkdir project
```

Multiple:

```bash
mkdir frontend backend
```

Nested directories:

```bash
mkdir -p project/src/components
```

---

# 9. touch

Empty file create:

```bash
touch app.py
```

Multiple:

```bash
touch index.html style.css script.js
```

---

# 10. cat

File content:

```bash
cat file.txt
```

Multiple files:

```bash
cat file1.txt file2.txt
```

Create file:

```bash
cat > file.txt
```

Type content and press:

```text
Ctrl + D
```

---

# 11. less

Large file read:

```bash
less file.txt
```

Exit:

```text
q
```

Search:

```text
/text
```

---

# 12. head

First lines:

```bash
head file.txt
```

First 20 lines:

```bash
head -n 20 file.txt
```

---

# 13. tail

Last lines:

```bash
tail file.txt
```

Last 20:

```bash
tail -n 20 file.txt
```

Live logs:

```bash
tail -f app.log
```

Exit:

```text
Ctrl + C
```

---

# 14. cp

Copy file:

```bash
cp file.txt backup.txt
```

Copy directory:

```bash
cp -r project project_backup
```

---

# 15. mv

Rename:

```bash
mv old.txt new.txt
```

Move:

```bash
mv file.txt Documents/
```

---

# 16. rm

Delete file:

```bash
rm file.txt
```

Delete directory:

```bash
rm -r project
```

Force:

```bash
rm -rf project
```

⚠️ `rm -rf` carefully use karo.

---

# 17. rmdir

Empty directory delete:

```bash
rmdir empty_folder
```

Non-empty folder ke liye:

```bash
rm -r folder
```

---

# 18. clear

Terminal clear:

```bash
clear
```

Shortcut:

```text
Ctrl + L
```

---

# 19. man

Command manual:

```bash
man ls
```

Example:

```bash
man chmod
```

Exit:

```text
q
```

---

# 20. Command Help

Many commands:

```bash
ls --help
```

```bash
cp --help
```

```bash
grep --help
```

---

# 21. File Paths

Example:

```text
/home/adnan/project/app.py
```

Components:

```text
/
└── home
    └── adnan
        └── project
            └── app.py
```

---

# 22. Absolute Path

Full path:

```bash
/home/adnan/project/app.py
```

Starts from:

```text
/
```

---

# 23. Relative Path

Current directory se path:

```bash
project/app.py
```

Parent:

```bash
../app.py
```

---

# 24. Hidden Files

Linux mein `.` se start hone wali files hidden hoti hain.

Example:

```text
.env
.git
.bashrc
```

See:

```bash
ls -a
```

---

# 25. Wildcards

All files:

```bash
ls *
```

Python files:

```bash
ls *.py
```

Text files:

```bash
ls *.txt
```

Single character:

```bash
ls file?.txt
```

---

# 26. grep

Text search:

```bash
grep "hello" file.txt
```

Case-insensitive:

```bash
grep -i "hello" file.txt
```

Line numbers:

```bash
grep -n "hello" file.txt
```

Recursive:

```bash
grep -r "hello" .
```

---

# 27. find

File search:

```bash
find . -name "app.py"
```

All Python files:

```bash
find . -name "*.py"
```

Directories:

```bash
find . -type d
```

Files:

```bash
find . -type f
```

---

# 28. locate

```bash
locate app.py
```

Depending on distribution, `locate` may need to be installed and its database updated.

---

# 29. wc

Lines:

```bash
wc -l file.txt
```

Words:

```bash
wc -w file.txt
```

Characters:

```bash
wc -m file.txt
```

---

# 30. sort

```bash
sort names.txt
```

Reverse:

```bash
sort -r names.txt
```

Numeric:

```bash
sort -n numbers.txt
```

---

# 31. uniq

Remove adjacent duplicate lines:

```bash
uniq file.txt
```

Count:

```bash
uniq -c file.txt
```

Usually sort first:

```bash
sort file.txt | uniq
```

---

# 32. cut

Example:

```bash
cut -d "," -f 1 users.csv
```

Meaning:

```text
-d "," → delimiter
-f 1   → first field
```

---

# 33. tee

Output screen + file:

```bash
echo "Hello" | tee output.txt
```

Append:

```bash
echo "Hello" | tee -a output.txt
```

---

# 34. Pipe

Pipe `|` ek command ka output next command ko deta hai.

Example:

```bash
ls | grep ".py"
```

Flow:

```text
ls
 ↓
Output
 ↓
grep
 ↓
Filtered Output
```

Another:

```bash
cat users.txt | grep "Adnan"
```

---

# 35. Redirection

Output file mein:

```bash
ls > files.txt
```

Append:

```bash
ls >> files.txt
```

Input:

```bash
sort < names.txt
```

Error redirect:

```bash
command 2> error.log
```

Output + error:

```bash
command > output.log 2>&1
```

---

# 36. Command Chaining

AND:

```bash
mkdir project && cd project
```

Agar first command successful hai tab second chalega.

OR:

```bash
command1 || command2
```

Sequential:

```bash
command1 ; command2
```

---

# 37. echo

```bash
echo "Hello"
```

Variable:

```bash
echo $USER
```

---

# 38. Environment Variables

See:

```bash
env
```

Specific:

```bash
echo $HOME
```

Common variables:

```text
$HOME
$USER
$SHELL
$PATH
$PWD
```

---

# 39. export

Temporary environment variable:

```bash
export APP_ENV=development
```

Check:

```bash
echo $APP_ENV
```

Child processes can inherit exported variables.

---

# 40. PATH

Check:

```bash
echo $PATH
```

PATH tells shell where to search for executable commands.

Example:

```text
/usr/local/bin
/usr/bin
/bin
```

Find command location:

```bash
which python
```

or:

```bash
command -v python
```

---

# 41. Users

Current user:

```bash
whoami
```

User ID:

```bash
id
```

Logged-in users:

```bash
who
```

---

# 42. Groups

Current groups:

```bash
groups
```

Detailed:

```bash
id
```

---

# 43. sudo

Administrative command:

```bash
sudo command
```

Example:

```bash
sudo apt update
```

`sudo` ka matlab hai command ko elevated privileges ke saath run karna.

---

# 44. File Permissions

Example:

```text
-rwxr-xr--
```

Breakdown:

```text
-   rwx   r-x   r--
│    │     │     │
│   user  group others
│
file
```

Permission:

```text
r = read
w = write
x = execute
```

---

# 45. Permission Numbers

```text
r = 4
w = 2
x = 1
```

Examples:

```text
rwx = 7
rw- = 6
r-x = 5
r-- = 4
```

---

# 46. chmod

Make executable:

```bash
chmod +x script.sh
```

Numeric:

```bash
chmod 755 script.sh
```

Meaning:

```text
7 → owner  → rwx
5 → group  → r-x
5 → others → r-x
```

Private file:

```bash
chmod 600 secret.txt
```

Meaning:

```text
owner → read/write
others → no access
```

---

# 47. chown

Change owner:

```bash
sudo chown adnan file.txt
```

Owner + group:

```bash
sudo chown adnan:developers file.txt
```

Recursive:

```bash
sudo chown -R adnan:developers project/
```

Use carefully.

---

# 48. chgrp

Change group:

```bash
sudo chgrp developers file.txt
```

---

# 49. Process

Running programs are processes.

See processes:

```bash
ps
```

All processes:

```bash
ps aux
```

Search:

```bash
ps aux | grep python
```

---

# 50. top

Real-time processes:

```bash
top
```

Exit:

```text
q
```

---

# 51. htop

If installed:

```bash
htop
```

It provides a more interactive process view.

---

# 52. kill

Find PID:

```bash
ps aux | grep python
```

Kill:

```bash
kill PID
```

Force kill:

```bash
kill -9 PID
```

Prefer normal `kill` first; `-9` should be a last resort when appropriate.

---

# 53. Jobs

Background jobs:

```bash
jobs
```

---

# 54. Background Process

Run command in background:

```bash
python app.py &
```

Bring foreground:

```bash
fg
```

Suspend current process:

```text
Ctrl + Z
```

Continue in background:

```bash
bg
```

---

# 55. nohup

Keep process running after terminal closes:

```bash
nohup python app.py &
```

Output often goes to:

```text
nohup.out
```

For production services, prefer a proper service manager instead of relying on `nohup`.

---

# 56. systemctl

Systemd services manage karne ke liye:

```bash
systemctl status nginx
```

Start:

```bash
sudo systemctl start nginx
```

Stop:

```bash
sudo systemctl stop nginx
```

Restart:

```bash
sudo systemctl restart nginx
```

Enable on boot:

```bash
sudo systemctl enable nginx
```

Disable:

```bash
sudo systemctl disable nginx
```

---

# 57. journalctl

System logs:

```bash
journalctl
```

Specific service:

```bash
journalctl -u nginx
```

Recent logs:

```bash
journalctl -u nginx -n 50
```

Follow:

```bash
journalctl -u nginx -f
```

---

# 58. Disk Space

Overall disk:

```bash
df -h
```

Directory size:

```bash
du -sh .
```

All directories:

```bash
du -h --max-depth=1
```

---

# 59. free

RAM:

```bash
free -h
```

---

# 60. uptime

System uptime:

```bash
uptime
```

---

# 61. uname

Kernel/system info:

```bash
uname -a
```

Kernel version:

```bash
uname -r
```

---

# 62. hostname

```bash
hostname
```

Detailed:

```bash
hostnamectl
```

---

# 63. Networking Basics

Check network interfaces:

```bash
ip addr
```

Short:

```bash
ip -br addr
```

---

# 64. IP Address

```bash
ip addr
```

Look for:

```text
inet
```

Example:

```text
192.168.1.10
```

---

# 65. Routing

```bash
ip route
```

---

# 66. ping

Connectivity test:

```bash
ping google.com
```

Stop:

```text
Ctrl + C
```

---

# 67. curl

HTTP request:

```bash
curl https://example.com
```

Headers:

```bash
curl -I https://example.com
```

GET API:

```bash
curl http://localhost:5000/api/users
```

POST JSON:

```bash
curl \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"name":"Adnan"}' \
  http://localhost:5000/api/users
```

---

# 68. wget

Download:

```bash
wget https://example.com/file.zip
```

---

# 69. ss

Check listening ports:

```bash
ss -tuln
```

With processes:

```bash
sudo ss -tulpn
```

---

# 70. DNS

Resolve domain:

```bash
getent hosts example.com
```

If available:

```bash
dig example.com
```

or:

```bash
nslookup example.com
```

---

# 71. Package Management

Different distributions use different package managers.

```text
Ubuntu/Debian → apt
Arch          → pacman
Fedora        → dnf
```

---

# 72. APT

Update package information:

```bash
sudo apt update
```

Upgrade:

```bash
sudo apt upgrade
```

Install:

```bash
sudo apt install nginx
```

Remove:

```bash
sudo apt remove nginx
```

Search:

```bash
apt search nginx
```

---

# 73. Pacman

Arch Linux:

Update:

```bash
sudo pacman -Syu
```

Install:

```bash
sudo pacman -S nginx
```

Remove:

```bash
sudo pacman -R nginx
```

Search:

```bash
pacman -Ss nginx
```

Installed package:

```bash
pacman -Q
```

---

# 74. AUR

Arch users often use an AUR helper such as:

```bash
yay
```

Example:

```bash
yay -S package-name
```

Review AUR package/build instructions before installing third-party packages.

---

# 75. Mounting

See disks:

```bash
lsblk
```

Filesystem information:

```bash
lsblk -f
```

Mounted filesystems:

```bash
findmnt
```

---

# 76. Archive Files

Create tar:

```bash
tar -cvf archive.tar project/
```

Extract:

```bash
tar -xvf archive.tar
```

---

# 77. tar.gz

Create:

```bash
tar -czvf project.tar.gz project/
```

Extract:

```bash
tar -xzvf project.tar.gz
```

Options:

```text
c = create
x = extract
v = verbose
f = file
z = gzip
```

---

# 78. zip

Install if needed:

```bash
sudo apt install zip unzip
```

Create:

```bash
zip -r project.zip project/
```

Extract:

```bash
unzip project.zip
```

---

# 79. SSH

Connect to remote server:

```bash
ssh username@server_ip
```

Example:

```bash
ssh root@192.168.1.100
```

---

# 80. SSH Key

Generate:

```bash
ssh-keygen -t ed25519
```

Default location:

```text
~/.ssh/
```

Common files:

```text
id_ed25519
id_ed25519.pub
```

Never share:

```text
id_ed25519
```

Public key:

```text
id_ed25519.pub
```

can be added to authorized services/servers.

---

# 81. SSH Public Key Login

Copy key:

```bash
ssh-copy-id username@server
```

Then:

```bash
ssh username@server
```

---

# 82. SCP

Copy local → remote:

```bash
scp file.txt user@server:/home/user/
```

Copy remote → local:

```bash
scp user@server:/home/user/file.txt .
```

Directory:

```bash
scp -r project/ user@server:/home/user/
```

---

# 83. rsync

Efficient file synchronization:

```bash
rsync -av project/ backup/
```

Remote:

```bash
rsync -av project/ user@server:/home/user/project/
```

---

# 84. Git

Check version:

```bash
git --version
```

Initialize:

```bash
git init
```

Status:

```bash
git status
```

Add:

```bash
git add .
```

Commit:

```bash
git commit -m "Initial commit"
```

---

# 85. Git Remote

```bash
git remote -v
```

Add:

```bash
git remote add origin <repository-url>
```

Push:

```bash
git push -u origin main
```

Pull:

```bash
git pull origin main
```

---

# 86. Git Branch

Create:

```bash
git branch feature
```

Switch:

```bash
git switch feature
```

Create + switch:

```bash
git switch -c feature
```

List:

```bash
git branch
```

---

# 87. Python

Check:

```bash
python --version
```

Sometimes:

```bash
python3 --version
```

Location:

```bash
which python
```

---

# 88. Python Virtual Environment

Create:

```bash
python -m venv .venv
```

Activate:

```bash
source .venv/bin/activate
```

Deactivate:

```bash
deactivate
```

Install:

```bash
pip install flask
```

Requirements:

```bash
pip freeze > requirements.txt
```

Install requirements:

```bash
pip install -r requirements.txt
```

---

# 89. Node.js

Check:

```bash
node --version
```

npm:

```bash
npm --version
```

Install dependencies:

```bash
npm install
```

Run:

```bash
npm run dev
```

---

# 90. Ports

A port identifies a network endpoint used by a service.

Examples:

```text
22   → SSH
53   → DNS
80   → HTTP
443  → HTTPS
3000 → Common development server
5000 → Common Flask development server
5432 → PostgreSQL
```

Check port:

```bash
sudo ss -tulpn | grep :5000
```

---

# 91. Process + Port

Find process using port:

```bash
sudo ss -tulpn | grep :8000
```

Alternative:

```bash
sudo lsof -i :8000
```

---

# 92. Cron

Scheduled tasks.

Edit:

```bash
crontab -e
```

List:

```bash
crontab -l
```

Format:

```text
minute hour day month weekday command
```

Example:

```cron
0 2 * * * /home/user/backup.sh
```

Meaning:

```text
Every day at 2:00 AM
```

---

# 93. Logs

Common log directory:

```text
/var/log/
```

View:

```bash
ls /var/log
```

Example:

```bash
sudo tail -f /var/log/syslog
```

The exact logs depend on the distribution and service.

---

# 94. Bash History

Show history:

```bash
history
```

Search history:

```bash
history | grep git
```

Run previous command:

```bash
!!
```

Run command by history number:

```bash
!123
```

---

# 95. Useful Shortcuts

```text
Ctrl + C → stop command
Ctrl + Z → suspend command
Ctrl + L → clear screen
Ctrl + D → EOF / logout
Ctrl + R → search history
Tab      → autocomplete
↑        → previous command
↓        → next command
```

---

# 96. Alias

Create temporary alias:

```bash
alias ll="ls -lah"
```

Now:

```bash
ll
```

For permanent aliases, add them to your shell configuration file such as:

```text
~/.bashrc
```

or:

```text
~/.zshrc
```

Then reload:

```bash
source ~/.bashrc
```

---

# 97. Which Command?

Find executable:

```bash
which python
```

Better general form:

```bash
command -v python
```

---

# 98. File Information

```bash
file app.py
```

Detailed metadata:

```bash
stat app.py
```

---

# 99. Disk/File Cleanup

Find large files:

```bash
find . -type f -size +100M
```

Find large directories:

```bash
du -h --max-depth=1 | sort -h
```

---

# 100. Bash Script

Create:

```bash
touch script.sh
```

Content:

```bash
#!/bin/bash

echo "Hello Linux"
```

Make executable:

```bash
chmod +x script.sh
```

Run:

```bash
./script.sh
```

---

# 101. Bash Variables

```bash
name="Adnan"

echo "$name"
```

Important:

No spaces:

```bash
name="Adnan"
```

Not:

```bash
name = "Adnan"
```

---

# 102. User Input

```bash
#!/bin/bash

read -p "Enter your name: " name

echo "Hello $name"
```

---

# 103. If Condition

```bash
if [ "$age" -ge 18 ]; then
    echo "Adult"
else
    echo "Minor"
fi
```

Common operators:

```text
-eq → equal
-ne → not equal
-gt → greater than
-lt → less than
-ge → greater/equal
-le → less/equal
```

---

# 104. File Conditions

```bash
if [ -f "app.py" ]; then
    echo "File exists"
fi
```

Directory:

```bash
if [ -d "project" ]; then
    echo "Directory exists"
fi
```

---

# 105. For Loop

```bash
for file in *.py
do
    echo "$file"
done
```

---

# 106. While Loop

```bash
count=1

while [ $count -le 5 ]
do
    echo $count
    count=$((count + 1))
done
```

---

# 107. Bash Function

```bash
greet() {
    echo "Hello $1"
}

greet "Adnan"
```

Output:

```text
Hello Adnan
```

---

# 108. Command Substitution

```bash
current_dir=$(pwd)

echo "$current_dir"
```

---

# 109. Exit Status

Check last command status:

```bash
echo $?
```

Usually:

```text
0 → success
non-zero → error/failure
```

---

# 110. Troubleshooting Flow

When command fails:

```text
1. Read error message
        ↓
2. Check command syntax
        ↓
3. Check current directory
        ↓
4. Check file exists
        ↓
5. Check permissions
        ↓
6. Check process
        ↓
7. Check port
        ↓
8. Check logs
        ↓
9. Check network
        ↓
10. Search documentation
```

---

# 111. "Permission Denied"

Check:

```bash
ls -l file
```

If executable script:

```bash
chmod +x script.sh
```

If access problem:

```bash
ls -ld directory
```

Don't blindly use:

```bash
chmod 777
```

---

# 112. "Command Not Found"

Check:

```bash
command -v command-name
```

Check PATH:

```bash
echo $PATH
```

Check package:

```bash
which command-name
```

Then install using the appropriate package manager if needed.

---

# 113. "Address Already in Use"

Example:

```text
Address already in use
```

Check port:

```bash
sudo ss -tulpn | grep :5000
```

Find process:

```bash
sudo lsof -i :5000
```

Stop the relevant process/service appropriately.

---

# 114. Server Not Responding

Check:

```bash
systemctl status service-name
```

Check port:

```bash
ss -tulpn
```

Check logs:

```bash
journalctl -u service-name
```

Test locally:

```bash
curl http://localhost:PORT
```

---

# 115. Important Linux Directories

## `/`

Root of filesystem.

```text
/
```

## `/home`

Normal users' home directories.

```text
/home/adnan
```

## `/root`

Root user's home directory.

## `/etc`

System configuration.

```text
/etc/ssh/
/etc/nginx/
```

## `/var`

Variable data.

```text
/var/log/
/var/lib/
```

## `/tmp`

Temporary files.

## `/usr`

Applications, libraries and other user-space system files.

## `/opt`

Optional/additional application software.

## `/dev`

Device files.

## `/proc`

Virtual filesystem exposing process/kernel information.

## `/sys`

Kernel/device information.

---

# 116. Home Directory

```bash
cd ~
```

Check:

```bash
echo $HOME
```

---

# 117. Root User

Root has extensive system privileges.

Check:

```bash
whoami
```

Do not work as root unnecessarily.

Prefer:

```bash
sudo command
```

when administrative privileges are actually required.

---

# 118. Linux File Descriptor Basics

Common descriptors:

```text
0 → stdin
1 → stdout
2 → stderr
```

Example:

```bash
command > output.txt
```

stdout:

```text
1
```

Error:

```bash
command 2> error.txt
```

Both:

```bash
command > output.txt 2>&1
```

---

# 119. Useful One-Liners

Find Python files:

```bash
find . -name "*.py"
```

Search code:

```bash
grep -r "def login" .
```

Find process:

```bash
ps aux | grep python
```

Check port:

```bash
ss -tulpn | grep :8000
```

Check disk:

```bash
df -h
```

Check RAM:

```bash
free -h
```

Check current directory:

```bash
pwd
```

List hidden files:

```bash
ls -la
```

---

# 120. Daily Developer Workflow

```text
Open Terminal
      ↓
pwd
      ↓
ls
      ↓
cd project
      ↓
git status
      ↓
Activate environment
      ↓
Run application
      ↓
Edit code
      ↓
Check logs
      ↓
Test API
      ↓
git add
      ↓
git commit
      ↓
git push
```

---

# 121. Linux + Flask Workflow

```bash
cd my-flask-app

source .venv/bin/activate

export FLASK_APP=app.py

flask run
```

Typical development server:

```text
http://127.0.0.1:5000
```

---

# 122. Linux + FastAPI Workflow

```bash
cd my-fastapi-app

source .venv/bin/activate

uvicorn app:app --reload
```

Typical development server:

```text
http://127.0.0.1:8000
```

---

# 123. Linux + React Workflow

```bash
cd frontend

npm install

npm run dev
```

Typical Vite development server:

```text
http://localhost:5173
```

---

# 124. Linux + Next.js Workflow

```bash
cd next-app

npm install

npm run dev
```

Typical development server:

```text
http://localhost:3000
```

---

# 125. Linux + PostgreSQL

Check PostgreSQL service:

```bash
systemctl status postgresql
```

Start:

```bash
sudo systemctl start postgresql
```

Connect:

```bash
psql -U postgres
```

List databases:

```sql
\l
```

Connect database:

```sql
\c mydatabase
```

List tables:

```sql
\dt
```

Exit:

```sql
\q
```

---

# 126. Linux Developer Stack

```text
Linux
│
├── Terminal
├── Bash
├── Git
├── Python
├── Node.js
├── PostgreSQL
├── Docker
├── SSH
└── VS Code
```

---

# 127. Linux Mental Model

```text
User
 ↓
Terminal
 ↓
Shell
 ↓
Command
 ↓
Kernel
 ↓
Hardware / Files / Network / Processes
```

---

# 128. Most Important Commands

If you're a beginner, first memorize these:

```bash
pwd
ls
cd
mkdir
touch
cat
cp
mv
rm
grep
find
chmod
chown
sudo
ps
top
kill
systemctl
journalctl
df
du
free
ip
ping
curl
ss
apt
pacman
tar
ssh
scp
git
```

---

# 129. 20 Commands to Learn First

```text
01. pwd
02. ls
03. cd
04. mkdir
05. touch
06. cat
07. cp
08. mv
09. rm
10. grep
11. find
12. chmod
13. sudo
14. ps
15. kill
16. df
17. du
18. curl
19. ssh
20. git
```

---

# 130. Linux Cheat Sheet

## Navigation

```bash
pwd
ls
ls -la
cd folder
cd ..
cd ~
cd -
```

## Files

```bash
touch file
cat file
cp file copy
mv file new
rm file
mkdir folder
rm -r folder
```

## Search

```bash
grep "text" file
find . -name "*.py"
```

## Permissions

```bash
chmod +x script.sh
chmod 755 script.sh
chown user:group file
```

## Processes

```bash
ps aux
top
kill PID
jobs
```

## Services

```bash
systemctl status service
sudo systemctl start service
sudo systemctl stop service
sudo systemctl restart service
```

## Network

```bash
ip addr
ip route
ping example.com
curl example.com
ss -tulpn
```

## Packages

Ubuntu/Debian:

```bash
sudo apt update
sudo apt install package
sudo apt upgrade
```

Arch:

```bash
sudo pacman -Syu
sudo pacman -S package
```

## Archives

```bash
tar -czvf archive.tar.gz folder/
tar -xzvf archive.tar.gz
```

## SSH

```bash
ssh user@server
scp file user@server:/path/
```

## Git

```bash
git status
git add .
git commit -m "message"
git pull
git push
```

---

# 131. Linux Golden Rules

```text
1. `pwd` se pata karo tum kahan ho.
2. `ls` se dekho kya hai.
3. `cd` se directory change karo.
4. `rm` carefully use karo.
5. `rm -rf` blindly mat chalao.
6. `sudo` sirf jab zarurat ho tab use karo.
7. `chmod 777` ko default solution mat banao.
8. Secrets ko public files/Git mein mat rakho.
9. Processes aur ports ko samajhkar kill karo.
10. Production mein proper service manager use karo.
11. Logs error solve karne ka first source hain.
12. Package manager ke according command use karo.
13. SSH private key kabhi share mat karo.
14. Root ke roop mein unnecessary kaam mat karo.
15. Error message ko pehle dhyan se padho.
```

---

# 132. Learning Roadmap

## Level 1

```text
Terminal
 ↓
pwd
ls
cd
mkdir
touch
cat
cp
mv
rm
```

## Level 2

```text
grep
find
pipe
redirection
permissions
chmod
sudo
```

## Level 3

```text
processes
ports
networking
systemctl
logs
packages
```

## Level 4

```text
SSH
Git
Python
Node.js
PostgreSQL
Docker
```

## Level 5

```text
Bash scripting
Servers
Nginx
Reverse Proxy
CI/CD
Monitoring
Security
```

---

# 🚀 Final Linux Architecture

```text
                         LINUX
                           │
          ┌────────────────┼────────────────┐
          │                │                │
       FILE SYSTEM      PROCESSES        NETWORK
          │                │                │
       Files/Folders    ps/top/kill      ip/curl/ss
          │                │                │
       Permissions       Services          Ports
          │                │                │
     chmod/chown       systemctl        Firewall
          │                │                │
          └────────────────┼────────────────┘
                           │
                         SHELL
                           │
                     Bash / Zsh
                           │
                     Commands
                           │
              ┌────────────┼────────────┐
              │            │            │
             Git         Python       Node.js
              │            │            │
              └────────────┼────────────┘
                           │
                    Developer Workflow
                           │
          ┌────────────────┼────────────────┐
          │                │                │
        Flask           Next.js         PostgreSQL
          │                │                │
          └────────────────┼────────────────┘
                           │
                        Server
```

# END
