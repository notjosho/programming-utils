# Linux Terminal Commands

**Resources:**
- [Linux Command Line Basics](https://www.digitalocean.com/community/tutorials/linux-commands)
- [The Linux Command Line Book](http://linuxcommand.org/tlcl.php)
- [ExplainShell - Command Explanations](https://explainshell.com/)

## Basic Concepts

### Understanding Paths
```bash
/                   # Root directory (top of filesystem)
/home/username      # User's home directory
~                   # Shortcut for your home directory
.                   # Current directory
..                  # Parent directory (one level up)
./file.txt          # File in current directory
../file.txt         # File in parent directory
../../folder        # Two levels up, then into folder
```

### Absolute vs Relative Paths
- **Absolute path**: Starts from root (`/home/user/documents/file.txt`)
- **Relative path**: Starts from current location (`documents/file.txt` or `./documents/file.txt`)

### sudo (Super User Do)
`sudo` runs commands with administrator privileges. Required for:
- Installing software: `sudo apt install package`
- Modifying system files: `sudo nano /etc/hosts`
- Changing system settings: `sudo chmod 755 /usr/bin/script`
- Managing services: `sudo systemctl restart nginx`

**Warning**: Be careful with sudo - it can modify or break your system!

## Navigation
```bash
pwd                 # Print working directory
ls                  # List files
ls -la              # List with details and hidden files
cd /path/to/dir     # Change directory
cd ..               # Go up one directory
cd ~                # Go to home directory
```

## File Operations
```bash
touch file.txt      # Create empty file
mkdir dirname       # Create directory
cp file.txt dest/   # Copy file
mv file.txt dest/   # Move/rename file
rm file.txt         # Remove file
rm -rf dirname/     # Remove directory recursively
```

## File Viewing
```bash
cat file.txt        # Display file content
less file.txt       # View file with pagination
head file.txt       # Show first 10 lines
tail file.txt       # Show last 10 lines
grep "pattern" file # Search in file
```

## Useful Shortcuts
```bash
Ctrl+C              # Cancel current command
Ctrl+Z              # Suspend current command
Ctrl+L              # Clear screen
Ctrl+R              # Search command history
!!                  # Run last command
history             # Show command history
```

## Text Processing
```bash
grep "text" file    # Search for text in file
grep -r "text" dir/ # Recursive search
find . -name "*.py" # Find files by name
wc -l file.txt      # Count lines in file
sort file.txt       # Sort file contents
uniq file.txt       # Remove duplicate lines
```

# Yet to see
## Permissions
File permissions control who can read, write, or execute files. Linux uses a 3-digit system: owner, group, others.

```bash
ls -l file.txt      # View file permissions (shows -rwxr-xr--)
chmod 755 file      # Owner: read/write/execute, Group/Others: read/execute
chmod +x script.sh  # Make file executable for all users
chmod u+w file      # Add write permission for owner (user)
chmod g-r file      # Remove read permission for group
chown user:group file # Change ownership to user and group
sudo chmod 644 file # Need sudo for system files (owner: rw, others: r)
```

**Permission numbers:**
- 7 = read + write + execute (4+2+1)
- 6 = read + write (4+2)
- 5 = read + execute (4+1)
- 4 = read only

## Process Management
Processes are running programs. You can monitor, control, and terminate them.

```bash
ps aux              # List all running processes with details
ps aux | grep python # Find processes containing "python"
top                 # Real-time process viewer (press 'q' to quit)
htop                # Better version of top (if installed)

# Finding process IDs
pgrep firefox       # Get PID of firefox processes
pidof python3       # Get PID of python3 processes

# Killing processes
kill 1234           # Terminate process with PID 1234 (graceful)
kill -9 1234        # Force kill process (immediate)
killall firefox     # Kill all processes named "firefox"
pkill python        # Kill processes matching "python"

# Background processes
python script.py &  # Run in background
jobs                # List background jobs
fg                  # Bring background job to foreground
nohup command &     # Run command that survives logout
```

**Common signals:**
- `kill PID` = SIGTERM (graceful shutdown)
- `kill -9 PID` = SIGKILL (immediate termination)
- `kill -15 PID` = SIGTERM (same as kill PID)

## File Compression
```bash
tar -czf archive.tar.gz folder/  # Create compressed archive
tar -xzf archive.tar.gz          # Extract archive
zip -r archive.zip folder/       # Create zip archive
unzip archive.zip                # Extract zip
```

## Network
```bash
ping google.com     # Test network connectivity
wget url            # Download file from URL
curl url            # Make HTTP request
ssh user@host       # Connect to remote server
```

## System Information
```bash
df -h               # Disk space usage
free -h             # Memory usage
uname -a            # System information
whoami              # Current user
date                # Current date and time
```


