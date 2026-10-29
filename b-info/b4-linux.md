# Linux & macOS CLI & Operational Matrix

## Track B — Public Knowledge & Reference Matrix (Unified CLI Systems Engineering Database)

- Document ID: MODERN-INFO-2026-10-07-LINUX-MAC-CLI-01.NotebookLM.Global
- Classification: Track B — Public Knowledge & Reference Matrix
- Target Environment: Cross-Platform / Ubuntu Linux CLI & macOS Terminal
- Scope: Exhaustive Cross-Platform CLI Command Reference, Package Management, File System Navigation, Troubleshooting, Diagnostics & Text Utilities

---

## Part 1: Unified CLI Operational Matrix (Foundation)

| Command / Concept | Scope / Category | Functional Mechanics & Purpose | Syntax & Example Usage | Operational Notes & Constraints | Linux / MacOS |
| :--- | :--- | :--- | :--- | :--- | :--- |
| apt vs. apt-get | Core Architecture | apt is a modern frontend built for human CLI usage. apt-get is a low-level backend engine built for script stability. | N/A (Architectural Concept) | Use apt for interactive terminal work. Use apt-get in headless automation. | Linux only <br>(macOS uses Homebrew brew) |
| apt update | Repo Synchronization | Queries online repositories and refreshes the local package index database. | sudo apt update<br><br>sudo apt-get update | Mandatory pre-flight command before installing or upgrading. | Linux only |
| apt upgrade | System Maintenance | Compares installed software against the local database and upgrades outdated packages. | sudo apt upgrade<br><br>sudo apt-get upgrade | Safe execution path; preserves current configurations. | Linux only |
| apt install | Software Provisioning | Fetches the target package binary and automatically resolves and installs dependencies. | sudo apt install package_name<br><br>Example: sudo apt install curl | Operates across official repositories. Requires sudo. | Linux only |
| apt remove / apt purge | Uninstallation | Uninstalls binaries while preserving configs (remove) or completely wipes binaries and configs (purge). | sudo apt remove nginx<br><br>sudo apt purge nginx | Use remove when custom configs must be retained. Purge is a full reset. | Linux only |
| apt autoremove | System Hygiene | Scans the system for orphaned packages and dependencies no longer required. | sudo apt autoremove | Best practice to execute periodically to free disk space. | Linux only |
| echo & $ | Shell / Output & Variables | echo prints text to stdout. $ acts as the parameter expansion operator for variables. | echo "Hello World"<br><br>echo $USER | Essential for debugging scripts and inspecting active environment variables. | Both <br>(POSIX standard) |
| expr | Arithmetic / Utilities | Evaluates basic integer arithmetic operations (addition, subtraction, multiplication, division). | expr 5 + 3<br><br>expr 10 % 3 | Spaces are mandatory around operators. $(( ... )) is preferred in modern Bash. | Both <br>(POSIX standard) |
| whoami | System Inspection | Displays the username of the currently logged-in effective user executing the command. | whoami | Useful in scripts to verify permission context and privilege levels. | Both |
| history | Shell Diagnostics | Displays the sequential list of previously executed commands in the shell session. | history<br><br>history \| grep apt | Allows quick auditing of past troubleshooting steps. | Both |
| clear | Terminal Hygiene | Clears the visible terminal display screen and resets the scroll buffer view. | clear | Purely visual interface cleanup. Shortcut is Ctrl+L. | Both |
| Navigation & Pathing (cd, .., Absolute vs Relative) | Filesystem Navigation | cd changes directory. .. points up. Absolute paths start from /; Relative paths start from current dir. | cd /var/log (Absolute)<br><br>cd ../etc (Relative) | Always verify current directory context via pwd before executing commands. | Both |
| ls / ls -l / ls -la | File / Directory Inspection | Lists directory contents. Supports long format (-l) and hidden files (-a). | ls -la<br><br>ls -lh /var/log | Use -l for long format, -a for hidden files, -h for human-readable sizes. | Both |
| cd dir / cd .. / cd - | Filesystem Navigation | Changes current working directory. .. goes up, - returns to previous directory. | cd /var/log<br><br>cd - | cd ~ navigates directly to the current user's home directory. | Both |
| pwd | Filesystem Navigation | Prints the absolute pathname of the current working directory to standard output. | pwd | Essential for orienting yourself before running relative path scripts. | Both |
| cat | File Inspection | Concatenates and displays the entire contents of text files directly to standard output. | cat file <br><br>cat file1 file2 | Avoid using on extremely large files to prevent flooding the terminal buffer. | Both |
| cat > file / cat >> file | File Management | Overwrites (>) or appends (>>) standard input into a target file. | cat > config.txt<br><br>cat log.txt >> master.log | Useful for quick inline file creation or stream capturing. | Both |
| head / head -n | File Inspection | Outputs the first part (default: first 10 lines) of specified files. | head /var/log/syslog<br><br>head -n 20 config.conf | Efficient for inspecting configuration file headers or initial log entries. | Both |
| tail / tail -n / tail -f | File Inspection | Outputs the final part of files. The -f flag enables real-time stream following. | tail -n 50 /var/log/auth.log<br><br>tail -f /var/log/syslog | The -f parameter is a standard diagnostic tool for monitoring live logs. | Both |
| more | File Inspection | Displays text file contents page-by-page, allowing forward-only scrolling. | more /etc/services | Press Spacebar to scroll down, q to exit. | Both |
| less | File Inspection | Advanced terminal pager allowing both forward and backward navigation through large files. | less /var/log/syslog | Preferred over more. Supports searching (/keyword) and arrow scrolling. | Both |
| touch | File Creation / Metadata | Creates a new empty file or updates access/modification timestamps. | touch new_script.sh | Frequently used to bootstrap empty log files, placeholder scripts, or test artifacts. | Both |
| mkdir | Directory Management | Creates new directories. Supports nested directory creation via the -p flag. | mkdir -p /var/log/homelab/audit | Always use -p to automatically create missing parent directories. | Both |
| cp | File Management (Copy) | Copies files or directory contents from source to destination. | cp file1 file2 | Use -r flag when copying entire directory trees recursively. | Both |
| mv | File Management (Move & Rename) | Moves files/directories or renames them if destination is in the same directory. | mv old_name.txt new_name.txt<br><br>mv file1 dir/file2 | Overwrites destination files without warning unless combined with -i. | Both |
| rm / rm -r / rm -rf | File / Directory Deletion | Removes files (rm) or recursively/forcefully removes entire directory trees (-r, -f). | rm temp_log.txt<br><br>rm -rf /var/log/old_lab/* | High-risk command. Misuse with root/sudo can destroy system integrity. | Both |
| date | System Info | Displays or sets the system date and time. | date | Useful in cron jobs, backups, and script timestamp generation. | Both |
| uptime | System Info | Shows how long the system has been running, current user count, and load averages. | uptime | Quick indicator of system health and load spikes. | Both |
| w | System Info | Displays currently logged-in users and what processes/commands they are executing. | w | Useful for security audits of active sessions. | Both |
| cat /proc/cpuinfo | System Info | Displays detailed CPU hardware specifications, core counts, and architecture features. | cat /proc/cpuinfo | Linux-specific virtual filesystem diagnostic file. | Linux only |
| cat /proc/meminfo | System Info | Displays detailed RAM and memory usage metrics. | cat /proc/meminfo | Linux-specific virtual filesystem diagnostic file. | Linux only |
| free -h | System Info | Displays total, used, and available RAM and swap space in human-readable units. | free -h | Essential diagnostic for checking memory pressure. | Both |
| du / du -sh | System Info / Storage | Estimates file and directory space usage. -s provides a summary, -h human-readable. | du -sh /var/log/ | Excellent tool for identifying space hogs on specific directories. | Both |
| df -h | System Info / Storage | Displays filesystem disk space usage breakdown across mounted filesystems. | df -h | Always use -h for human-readable sizes (GB/MB). | Both |
| uname -a | System Info | Prints system information including kernel release, version, machine architecture, and hostname. | uname -a | Quick check for OS version and kernel compatibility. | Both |
| tar (Archive & Compress) | Archive & Compress | Utility for archiving (-c), extracting (-x), listing contents (-t), and compressing with gzip (-z). | tar cvf archive.tar files<br><br>tar xvf archive.tar<br><br>tar zcvf archive.tar.gz dir | Tar options: c (create), x (extract), t (list), z (gzip), f (filename). | Both |
| ping | Networking | Sends ICMP ECHO_REQUEST packets to network hosts to test reachability. | ping host<br><br>ping 8.8.8.8 | Diagnostic tool for basic IP connectivity and latency check. | Both |
| whois | Networking | Fetches WHOIS domain registration and ownership records. | whois domain<br><br>whois example.com | Useful for domain auditing and reconnaissance. | Both |
| dig | Networking | DNS lookup utility used to query DNS name servers. Supports reverse lookups (-x). | dig domain<br><br>dig -x 8.8.8.8 | Essential tool for diagnosing DNS resolution issues. | Both |
| wget | Networking | Non-interactive network downloader. Supports background downloads, resumption (-c), and recursive mirroring (-r). | wget url<br><br>wget -c url<br><br>wget -r url | Robust tool for pulling files via HTTP, HTTPS, and FTP in scripts. | Both |
| curl | Networking | Command-line tool for transferring data with URLs. Outputs to stdout by default; can output to file (-o). | curl url<br><br>curl -o file.html url | Standard utility for API testing and fetching web payloads. | Both |
| ssh | Networking | Secure Shell protocol client for remote secure login and tunneling. Supports custom ports (-p) and SOCKS proxy (-D). | ssh user@host<br><br>ssh -p 2222 user@host<br><br>ssh -D 1080 user@host | Fundamental tool for remote infrastructure management. | Both |
| chmod | Permissions | Changes file and directory access permissions using symbolic modes or octal math. | chmod 755 file<br><br>chmod 644 file | Octal math values: Read(4), Write(2), Execute(1). Order: User / Group / Others. | Both |
| chown | Permissions | Changes the user and/or group ownership of files and directories. | sudo chown user:group file | Requires root privileges to transfer ownership between users. | Both |
| ps / ps aux | Processes | Displays active shell processes (ps) or a detailed snapshot of all running system processes (ps aux). | ps<br><br>ps aux | Essential for process auditing and locating runaway tasks. | Both |
| kill / killall | Processes | Terminates a process by its Process ID (kill pid) or terminates all processes matching a specific name (killall). | kill 1234<br><br>killall nginx | Use kill -9 pid for forced termination if a process hangs. | Both |
| grep | Search & Filtering | Searches for regular expression patterns in files (grep) or recursively across directories (grep -r). | grep pattern file<br><br>grep -r pattern dir | Core text processing tool for log analysis and debugging. | Both |
| locate / whereis | File Search | Finds instances of a file using a prebuilt database index (locate) or locates binary, source, and manual pages (whereis). | locate file<br><br>whereis app | Locate is extremely fast; whereis focuses on application binaries. | Both |
| man | Documentation | Displays the system manual pages for any given command or utility. | man command<br><br>man ssh | Built-in documentation reference system across UNIX-like systems. | Both |
| Pipes (\|) & Filtering | Power Tools | Passes the standard output of one command as standard input to another. | ps aux \| grep nginx | Core philosophy of UNIX pipelines for composable automation. | Both |

---

## Part 2: Linux Troubleshooting Matrix

| Troubleshooting Scenario | Diagnostic Check | Operational Mechanics & Purpose | Syntax & Example Usage | Operational Notes & Constraints | Linux / MacOS |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **1. CPU is 100%** | Check running process | Identifies top processes consuming CPU cycles. | top<br><br>ps aux --sort=-%cpu \| head | Allows identifying runaway processes. | Both |
| **2. Memory is full** | Check memory usage | Views memory consumption and top memory-hungry processes. | free -h<br><br>ps aux --sort=-%mem \| head | Identifies which applications or services are causing memory pressure. | Both |
| **3. Disk is full** | Check disk space & big folders | Views disk partition usage and lists large directories/files. | df -h<br><br>du -sh /var/* | Quickly locates source of disk saturation (e.g., in /var/log). | Both |
| **4. Website is not working** | Check service, port, local access | Verifies web server service status, port listening, and local reachability. | systemctl status nginx<br><br>ss -tulpn<br><br>curl localhost | Diagnostic path for confirming if Nginx/Apache is running and accessible locally. | Linux only |
| **5. SSH is not working** | Check port 22, service | Confirms SSH service status and port 22 binding. | ss -tulpn \| grep :22<br><br>systemctl status ssh | Standard local verification steps when remote SSH access fails. | Linux only |
| **6. Port is already in use** | Find the process using the port | Identifies the process binding a specific port. | ss -tulpn \| grep :80<br><br>lsof -i :80 | Essential for resolving port binding conflicts when starting services. | Both |
| **7. Permission denied** | Check permissions & ownership | Inspects current permission levels and owner/group of a file. | ls -l<br><br>chmod 755 file.sh<br><br>chown user:group file.sh | Resolves standard execution or access errors. Use ls -la to see hidden files. | Both |
| **8. DNS is not working** | Check DNS resolution | Verifies domain name resolution capability and local resolver configuration. | nslookup example.com<br><br>dig example.com<br><br>cat /etc/resolv.conf | Diagnostics for validating DNS functionality and resolver configuration. | Both |
| **9. Service keeps failing** | Check status and logs | Inspects service state and service-specific logs via journald. | systemctl status nginx<br><br>journalctl -u nginx | Comprehensive view for debugging failing or crash-looping systemd services. | Linux only |
| **10. Application logs need investigation** | Check live logs and search errors | Monitors logs in real-time or searches historical logs for errors. | tail -f /var/log/nginx/error.log<br><br>grep -i "error" app.log | Standard practice for analyzing application-specific failures and bugs. | Both |

---

## Part 3: Specialized & Lesser-Known Text Utilities

| Command / Tool | Scope / Category | Functional Mechanics & Purpose | Syntax & Example Usage | Operational Notes & Constraints | Linux / MacOS |
| :--- | :--- | :--- | :--- | :--- | :--- |
| tac | File Processing | Concatenates and prints files in reverse line order (last line first). | tac file.txt | Opposite of cat; ideal for reading logs in reverse chronological order. | Both <br>(coreutils) |
| rev | String Manipulation | Reverses the characters within each line of an input or stream. | echo "hello" \| rev | Reverses string order character-by-character per line. | Both |
| shuf | Randomization | Generates random permutations of input lines or shuffles file lines. | shuf file.txt | Useful for sample selection, testing datasets, or random line processing. | Both <br>(GNU coreutils) |
| nl | Text Formatting | Line numbering utility that writes input with line numbers added. | nl file.txt | More flexible than cat -n for custom numbering format styles. | Both |
| yes | Automation / Testing | Outputs a string repeatedly until terminated. | yes hello<br><br>yes \| apt-get upgrade | Frequently used to automate prompts expecting repeated 'y' confirmations. | Both |
| fold | Text Formatting | Wraps each input line to fit a specified maximum column width. | fold -w 20 file.txt | Prevents long lines from overflowing narrow screen buffers or terminal views. | Both |
| stat | File Metadata | Displays detailed file or filesystem status, including inode, access, modification, and change times. | stat myfile.txt | Provides significantly deeper metadata than standard ls -l output. | Both |
