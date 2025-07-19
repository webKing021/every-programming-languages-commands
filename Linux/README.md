# Linux Commands Reference

## File System Navigation

```bash
# Print working directory
pwd

# List directory contents
ls
ls -l     # Long format
ls -a     # Show hidden files
ls -la    # Long format with hidden files
ls -lh    # Human-readable file sizes
ls -lt    # Sort by modification time
ls -lr    # Reverse order
ls -R     # Recursive listing

# Change directory
cd /path/to/directory
cd ~      # Home directory
cd ..     # Parent directory
cd -      # Previous directory

# Create directory
mkdir directory_name
mkdir -p parent/child/grandchild  # Create parent directories as needed

# Remove directory
rmdir directory_name              # Remove empty directory
rm -r directory_name             # Remove directory and contents
rm -rf directory_name            # Force remove without confirmation

# Copy files/directories
cp source destination
cp -r source_dir destination_dir  # Copy directories recursively
cp -p file1 file2                # Preserve permissions
cp -a source destination         # Archive mode (preserve attributes)

# Move/rename files/directories
mv source destination

# Create symbolic link
ln -s target_path link_name

# Find files/directories
find /path/to/search -name "filename"
find /path/to/search -type f -name "*.txt"  # Find files
find /path/to/search -type d -name "*dir*"  # Find directories
find /path/to/search -mtime -7              # Modified in last 7 days
find /path/to/search -size +10M             # Larger than 10MB
find /path/to/search -exec command {} \;    # Execute command on each result

# Locate files (using database)
locate filename
updatedb                                    # Update locate database

# Show disk usage
du -h file_or_directory                     # Human-readable sizes
du -sh directory                            # Summary for directory
du -h --max-depth=1 /path                   # First level usage

# Show disk space
df -h                                       # Human-readable sizes
df -i                                       # Show inodes
```

## File Operations

```bash
# Create empty file
touch filename

# View file contents
cat filename
less filename                               # Paginated view
more filename                               # Simple pagination
head filename                               # First 10 lines
head -n 20 filename                         # First 20 lines
tail filename                               # Last 10 lines
tail -n 20 filename                         # Last 20 lines
tail -f filename                            # Follow file updates

# Count lines, words, characters
wc filename
wc -l filename                              # Count lines only
wc -w filename                              # Count words only
wc -c filename                              # Count bytes
wc -m filename                              # Count characters

# Compare files
diff file1 file2
diff -u file1 file2                         # Unified format
sdiff file1 file2                           # Side-by-side comparison
cmp file1 file2                             # Byte by byte comparison

# Sort file contents
sort filename
sort -r filename                            # Reverse order
sort -n filename                            # Numeric sort
sort -k 2 filename                          # Sort by second column

# Remove duplicates
uniq filename                               # Requires sorted input
sort filename | uniq                        # Sort and remove duplicates
uniq -c filename                            # Count occurrences

# Split files
split -l 100 filename prefix               # Split by lines
split -b 10M filename prefix               # Split by size

# Combine files
cat file1 file2 > combined_file

# Create file with content
cat > filename << EOF
content line 1
content line 2
EOF

# File permissions
chmod permissions filename
chmod 755 filename                          # rwxr-xr-x
chmod +x filename                           # Add execute permission
chmod -w filename                           # Remove write permission
chmod u+rwx,g+rx,o+r filename              # Symbolic mode

# Change file owner
chown user:group filename
chown -R user:group directory               # Recursive

# Change file timestamps
touch -a filename                           # Update access time
touch -m filename                           # Update modification time
touch -t 202301010000.00 filename          # Set specific time
```

## Text Processing

```bash
# Search file contents
grep pattern filename
grep -i pattern filename                    # Case-insensitive
grep -r pattern directory                   # Recursive search
grep -v pattern filename                    # Invert match
grep -l pattern files                       # List matching files only
grep -n pattern filename                    # Show line numbers
grep -A 2 pattern filename                  # Show 2 lines after match
grep -B 2 pattern filename                  # Show 2 lines before match
grep -C 2 pattern filename                  # Show 2 lines around match

# Regular expression search
grep -E "regex" filename                    # Extended regex
egrep "regex" filename                      # Same as grep -E

# Search and replace
sed 's/pattern/replacement/' filename
sed 's/pattern/replacement/g' filename      # Global replacement
sed -i 's/pattern/replacement/g' filename   # Edit file in place

# Advanced text processing
awk '{print $1}' filename                   # Print first column
awk -F: '{print $1}' filename              # Use : as delimiter
awk '{sum+=$1} END {print sum}' filename   # Sum first column

# Cut columns
cut -d: -f1 filename                       # First field, : delimiter
cut -c1-10 filename                         # Characters 1-10

# Join files
join file1 file2                           # Join on first column
join -1 2 -2 3 file1 file2                 # Join file1 col2 with file2 col3

# Translate characters
tr 'a-z' 'A-Z' < filename                  # Convert to uppercase
tr -d '\r' < filename                       # Remove carriage returns

# Format text
fmt filename                                # Reformat paragraphs
fmt -w 80 filename                          # Set width to 80 characters

# Count pattern occurrences
grep -o pattern filename | wc -l
```

## Process Management

```bash
# List processes
ps
ps aux                                      # All processes
ps -ef                                      # Full format
ps aux | grep process_name                  # Find specific process

# Process tree
pstree
pstree -p                                   # Show PIDs

# Interactive process viewer
top
htop                                        # Enhanced version

# Background processes
command &                                   # Run in background
nohup command &                             # Run immune to hangups

# Job control
jobs                                        # List jobs
bg %job_number                              # Background job
fg %job_number                              # Foreground job
Ctrl+Z                                      # Suspend process

# Kill processes
kill PID
kill -9 PID                                 # Force kill
killall process_name                        # Kill by name
pkill pattern                               # Kill by pattern

# Process priority
nice -n 10 command                          # Run with lower priority
renice +10 -p PID                           # Change priority

# Run at scheduled time
at 10:00 PM                                # Schedule job
batch                                       # Run when load permits

# Cron jobs
crontab -l                                  # List cron jobs
crontab -e                                  # Edit cron jobs

# System resource usage
free -h                                     # Memory usage
uptime                                      # Load average
iostat                                      # I/O statistics
vmstat                                      # Virtual memory statistics
mpstat                                      # CPU statistics
```

## User Management

```bash
# Current user info
whoami                                      # Current username
id                                          # User and groups info
groups                                      # Current user's groups

# User information
who                                         # Who is logged in
w                                           # Who is logged in and what they're doing
last                                        # Recent logins
lastlog                                     # Last login for all users

# Switch user
su username                                 # Switch user
su - username                               # Switch user with environment
sudo command                                # Execute as superuser
sudo -i                                     # Login as superuser

# User administration
useradd username                            # Create user
usermod -options username                   # Modify user
userdel username                            # Delete user
passwd username                             # Change password

# Group administration
groupadd groupname                          # Create group
groupmod -options groupname                 # Modify group
groupdel groupname                          # Delete group

# Add user to group
usermod -aG groupname username

# Change file ownership
chown user:group file
chown -R user:group directory               # Recursive
```

## System Information

```bash
# System info
uname -a                                    # All system info
hostname                                    # System hostname
uptime                                      # System uptime
date                                        # Current date and time
cal                                         # Calendar

# Hardware info
lscpu                                       # CPU info
lspci                                       # PCI devices
lsusb                                       # USB devices
lsblk                                       # Block devices
fdisk -l                                    # Disk partitions
df -h                                       # Disk usage
free -h                                     # Memory usage

# System logs
dmesg                                       # Kernel messages
cat /var/log/syslog                         # System log
cat /var/log/auth.log                       # Authentication log
journalctl                                  # systemd journal
journalctl -u service_name                  # Service logs

# System monitoring
top                                         # Process activity
htop                                        # Enhanced top
iotop                                       # I/O monitoring
netstat -tuln                               # Network connections
ss -tuln                                    # Socket statistics

# System load
uptime                                      # Load average
sar                                         # System activity reporter
```

## Networking

```bash
# Network interfaces
ifconfig                                    # Interface configuration
ip addr show                                # IP addresses
ip link show                                # Network interfaces

# Network connectivity
ping host                                   # ICMP echo
traceroute host                             # Trace route to host
tracepath host                              # Trace path to host
mtr host                                    # My traceroute

# DNS lookup
nslookup domain                             # Name server lookup
dig domain                                  # DNS lookup
host domain                                 # DNS lookup

# Network connections
netstat -tuln                               # Listening ports
netstat -tulanp                             # All connections with PID
ss -tuln                                    # Socket statistics
lsof -i                                     # List open files (network)

# Remote connections
ssh user@host                               # Secure shell
scp file user@host:/path                    # Secure copy (upload)
scp user@host:/path/file .                  # Secure copy (download)
rsync -av source destination                # Remote sync

# Network configuration
dhclient interface                          # Request DHCP address
route -n                                    # Routing table
ip route show                               # IP routing table

# Firewall (iptables)
iptables -L                                 # List rules
iptables -A CHAIN rule                      # Append rule

# Network scanning
nmap host                                   # Port scanning
```

## Package Management

### Debian/Ubuntu (apt)

```bash
# Update package lists
apt update

# Upgrade packages
apt upgrade
apt full-upgrade                            # Upgrade with package removal

# Install packages
apt install package_name

# Remove packages
apt remove package_name
apt purge package_name                      # Remove with configuration
apt autoremove                              # Remove unused dependencies

# Search packages
apt search keyword
apt-cache search keyword

# Package information
apt show package_name
apt-cache policy package_name

# List packages
apt list --installed
dpkg -l                                     # List all installed packages

# Package file information
dpkg -S /path/to/file                       # Find package owning file
dpkg -L package_name                        # List files in package
```

### Red Hat/Fedora (dnf/yum)

```bash
# Update package lists
dnf check-update
yum check-update

# Upgrade packages
dnf upgrade
yum update

# Install packages
dnf install package_name
yum install package_name

# Remove packages
dnf remove package_name
yum remove package_name

# Search packages
dnf search keyword
yum search keyword

# Package information
dnf info package_name
yum info package_name

# List packages
dnf list installed
yum list installed
rpm -qa                                     # List all installed packages

# Package file information
rpm -qf /path/to/file                       # Find package owning file
rpm -ql package_name                        # List files in package
```

### Arch Linux (pacman)

```bash
# Update package lists and upgrade
pacman -Syu

# Install packages
pacman -S package_name

# Remove packages
pacman -R package_name
pacman -Rs package_name                     # Remove with dependencies

# Search packages
pacman -Ss keyword

# Package information
pacman -Si package_name
pacman -Qi package_name                     # For installed packages

# List packages
pacman -Q                                   # List installed packages

# Package file information
pacman -Qo /path/to/file                    # Find package owning file
pacman -Ql package_name                     # List files in package
```

## Compression & Archives

```bash
# tar archives
tar -cf archive.tar files                   # Create tar archive
tar -xf archive.tar                         # Extract tar archive
tar -tf archive.tar                         # List contents

# tar with compression
tar -czf archive.tar.gz files               # Create tar.gz archive
tar -xzf archive.tar.gz                     # Extract tar.gz archive
tar -cjf archive.tar.bz2 files              # Create tar.bz2 archive
tar -xjf archive.tar.bz2                    # Extract tar.bz2 archive
tar -cJf archive.tar.xz files               # Create tar.xz archive
tar -xJf archive.tar.xz                     # Extract tar.xz archive

# zip archives
zip archive.zip files                       # Create zip archive
zip -r archive.zip directory                # Create recursive zip archive
unzip archive.zip                           # Extract zip archive
unzip -l archive.zip                        # List contents

# gzip compression
gzip file                                   # Compress file (replaces original)
gzip -k file                                # Keep original file
gunzip file.gz                              # Decompress file

# bzip2 compression
bzip2 file                                  # Compress file (replaces original)
bzip2 -k file                               # Keep original file
bunzip2 file.bz2                            # Decompress file

# xz compression
xz file                                     # Compress file (replaces original)
xz -k file                                  # Keep original file
unxz file.xz                                # Decompress file
```

## Shell Scripting

```bash
# Shebang
#!/bin/bash
#!/bin/sh

# Variables
VAR="value"
echo $VAR
echo "$VAR"
echo ${VAR}

# Command substitution
VAR=$(command)
VAR=`command`

# Arithmetic
result=$((1 + 2))
let result=1+2

# Conditionals
if [ condition ]; then
    commands
elif [ condition ]; then
    commands
else
    commands
fi

# Loops
for i in 1 2 3; do
    commands
done

for i in {1..10}; do
    commands
done

for ((i=0; i<10; i++)); do
    commands
done

while [ condition ]; do
    commands
done

until [ condition ]; do
    commands
done

# Functions
function_name() {
    commands
    return value
}

# Input/output redirection
command > file                              # Redirect stdout to file
command >> file                             # Append stdout to file
command 2> file                             # Redirect stderr to file
command &> file                             # Redirect both stdout and stderr
command < file                              # Read stdin from file
command1 | command2                         # Pipe stdout to stdin

# Exit status
echo $?                                     # Last command's exit status
command || echo "Failed"                    # Run if previous command failed
command && echo "Success"                   # Run if previous command succeeded

# Special parameters
$0                                          # Script name
$1, $2, ...                                 # Positional parameters
$#                                          # Number of positional parameters
$@                                          # All positional parameters
$*                                          # All positional parameters as one
$$                                          # Process ID of the script
$?                                          # Exit status of last command
```

## System Services

### systemd

```bash
# Service management
systemctl start service_name                # Start service
systemctl stop service_name                 # Stop service
systemctl restart service_name              # Restart service
systemctl reload service_name               # Reload configuration
systemctl status service_name               # Check status

# Enable/disable at boot
systemctl enable service_name               # Enable at boot
systemctl disable service_name              # Disable at boot

# System state
systemctl poweroff                          # Shutdown
systemctl reboot                            # Reboot
systemctl suspend                           # Suspend
systemctl hibernate                         # Hibernate

# List units
systemctl list-units                        # All active units
systemctl list-units --all                  # All units
systemctl list-units --type=service         # Only services

# Journal (logs)
journalctl                                  # All logs
journalctl -u service_name                  # Service logs
journalctl -f                               # Follow logs
journalctl --since="2023-01-01"             # Logs since date
journalctl --until="2023-01-02"             # Logs until date
journalctl -p err                           # Error logs
```

### SysVinit

```bash
# Service management
service service_name start                  # Start service
service service_name stop                   # Stop service
service service_name restart                # Restart service
service service_name status                 # Check status

# Enable/disable at boot
chkconfig service_name on                   # Enable at boot
chkconfig service_name off                  # Disable at boot
chkconfig --list                            # List services

# System state
shutdown -h now                             # Shutdown
shutdown -r now                             # Reboot
reboot                                      # Reboot
poweroff                                    # Shutdown
```

## Security & Permissions

```bash
# File permissions
chmod permissions file                      # Change file mode
chmod 755 file                              # rwxr-xr-x
chmod +x file                               # Add execute permission
chmod -w file                               # Remove write permission
chmod u+rwx,g+rx,o+r file                  # Symbolic mode

# Change file owner
chown user:group file                       # Change owner and group
chown -R user:group directory               # Recursive

# Default permissions
umask                                       # Display current umask
umask 022                                   # Set umask (rwxr-xr-x)

# Access control lists
getfacl file                                # Display ACL
setfacl -m u:user:rwx file                  # Modify ACL

# Security limits
ulimit -a                                   # Display all limits
ulimit -n 4096                              # Set file descriptor limit

# Firewall (iptables)
iptables -L                                 # List rules
iptables -A CHAIN rule                      # Append rule

# Firewall (firewalld)
firewall-cmd --state                        # Check state
firewall-cmd --get-default-zone             # Default zone
firewall-cmd --list-all                     # List all rules

# Firewall (ufw)
ufw status                                  # Check status
ufw allow 22/tcp                            # Allow SSH
ufw enable                                  # Enable firewall

# SELinux
getenforce                                  # Get enforcement mode
setenforce 1                                # Set enforcing mode
setenforce 0                                # Set permissive mode
```

## Miscellaneous

```bash
# Terminal multiplexer (screen)
screen                                      # Start screen
screen -S session_name                      # Start named session
screen -r                                   # Reattach
screen -r session_name                      # Reattach to named session
screen -ls                                  # List sessions
Ctrl+a d                                    # Detach
Ctrl+a c                                    # Create new window
Ctrl+a n                                    # Next window
Ctrl+a p                                    # Previous window

# Terminal multiplexer (tmux)
tmux                                        # Start tmux
tmux new -s session_name                    # Start named session
tmux attach                                 # Reattach
tmux attach -t session_name                 # Reattach to named session
tmux ls                                     # List sessions
Ctrl+b d                                    # Detach
Ctrl+b c                                    # Create new window
Ctrl+b n                                    # Next window
Ctrl+b p                                    # Previous window

# Schedule commands
at 10:00 PM                                # Schedule job
batch                                       # Run when load permits
crontab -e                                  # Edit cron jobs

# Environment variables
env                                         # Display all variables
export VAR=value                            # Set variable
echo $VAR                                   # Display variable

# Command history
history                                     # Show command history
!n                                          # Execute command number n
!!                                          # Execute last command
!string                                     # Execute last command starting with string
Ctrl+r                                      # Search history

# Help and documentation
man command                                 # Manual page
info command                                # Info documentation
command --help                              # Brief help
whatis command                              # One-line description
whereis command                             # Locate binary, source, manual

# System shutdown/reboot
shutdown -h now                             # Shutdown immediately
shutdown -r now                             # Reboot immediately
shutdown -h +10                             # Shutdown in 10 minutes
reboot                                      # Reboot
poweroff                                    # Shutdown
```