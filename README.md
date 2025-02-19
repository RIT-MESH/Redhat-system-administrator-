# Red Hat System Administration - From Basics to Advanced

## Table of Contents
1. Introduction to Linux
2. File System Hierarchy
3. Basic Linux Commands
4. User and Group Management
5. File Permissions and Ownership
6. Package Management with YUM/DNF
7. System Services and systemctl
8. Networking Basics
9. SSH and Remote Access
10. Disk Partitioning and Management
11. Logical Volume Management (LVM)
12. File System Creation and Mounting
13. Process Management
14. Cron Jobs and Automation
15. Shell Scripting Basics
16. Environment Variables
17. Red Hat Kickstart
18. SELinux Basics
19. Firewall Management with firewalld
20. Network Time Protocol (NTP)
21. Log Management with journalctl
22. Backup and Restore
23. Troubleshooting Boot Issues
24. Kernel Management
25. Network Bonding and Teaming
26. Advanced Shell Scripting
27. Ansible Basics
28. Containerization with Podman
29. Web Server Management (Apache/Nginx)
30. Database Management (MariaDB/PostgreSQL)
31. Email Server Configuration
32. DNS Server Configuration
33. DHCP Server Configuration
34. NFS and Samba File Sharing
35. Advanced SELinux Configuration
36. System Security and Hardening
37. Performance Monitoring and Tuning
38. Disaster Recovery Planning
39. High Availability with Pacemaker
40. Load Balancing with HAProxy
41. Virtualization with KVM
42. Cloud Integration with OpenStack
43. Advanced Networking (VLANs, VPNs)
44. Automation with Puppet
45. Advanced Log Analysis

---

## 1. Introduction to Linux
Linux is an open-source operating system that powers servers, desktops, and embedded systems.

### Example:
```bash
# Check the Linux version
cat /etc/os-release
```

---

## 2. File System Hierarchy
Understanding the Linux directory structure.

### Example:
```bash
# List root directories
ls /
```

---

## 3. Basic Linux Commands
Essential commands for navigating and managing Linux.

### Example:
```bash
# Display current directory
pwd

# List files in a directory
ls -lah

# Create a directory
mkdir my_folder

# Remove a file
rm myfile.txt
```

---

## 4. User and Group Management
Managing users and groups in Linux.

### Example:
```bash
# Add a new user
sudo useradd alice

# Set user password
sudo passwd alice

# Add a user to a group
sudo usermod -aG sudo alice
```

---

## 5. File Permissions and Ownership
Understanding file permissions and managing them.

### Example:
```bash
# View file permissions
ls -l myfile.txt

# Change file permissions
chmod 755 myfile.txt

# Change file ownership
chown alice:developers myfile.txt
```

---

## 6. Package Management with YUM/DNF
Installing and managing software packages.

### Example:
```bash
# Install a package
sudo dnf install httpd

# Remove a package
sudo dnf remove httpd
```

---

## 7. System Services and systemctl
Managing system services with systemctl.

### Example:
```bash
# Start a service
sudo systemctl start httpd

# Enable a service to start at boot
sudo systemctl enable httpd

# Check the status of a service
sudo systemctl status httpd
```

---

## 8. Networking Basics
Configuring and managing network settings.

### Example:
```bash
# Display network interfaces
ip a

# Assign an IP address
sudo ip addr add 192.168.1.100/24 dev eth0
```

---

## 9. SSH and Remote Access
Configuring SSH for remote access.

### Example:
```bash
# Connect to a remote server
ssh user@remote_host

# Copy files over SSH
scp file.txt user@remote_host:/home/user/
```

---

## 10. Disk Partitioning and Management
Creating and managing disk partitions.

### Example:
```bash
# View disk partitions
lsblk

# Create a new partition
fdisk /dev/sdb
```

---

## 11. Logical Volume Management (LVM)
LVM provides flexible disk management.

### Example:
```bash
# Create a physical volume
pvcreate /dev/sdb1

# Create a volume group
vgcreate my_vg /dev/sdb1

# Create a logical volume
lvcreate -L 10G -n my_lv my_vg
```

---

## 12. File System Creation and Mounting
Creating and mounting file systems.

### Example:
```bash
# Format a partition with ext4
mkfs.ext4 /dev/sdb1

# Mount the partition
mount /dev/sdb1 /mnt

# Unmount the partition
umount /mnt
```

---

## 13. Process Management
Managing system processes effectively.

### Example:
```bash
# List running processes
ps aux

# Find a process by name
pgrep apache

# Kill a process
kill -9 <PID>
```

---

## 14. Cron Jobs and Automation
Automating tasks using cron jobs.

### Example:
```bash
# Edit crontab
crontab -e

# Add a cron job to run a script every day at midnight
0 0 * * * /path/to/script.sh
```

---

## 15. Shell Scripting Basics
Writing basic shell scripts.

### Example:
```bash
# Create a simple script
echo -e "#!/bin/bash\necho Hello, World!" > script.sh

# Make it executable
chmod +x script.sh

# Run the script
./script.sh
```

---

## 16. Environment Variables
Using and managing environment variables.

### Example:
```bash
# Display environment variables
printenv

# Set an environment variable
export MY_VAR="Hello World"

# Use the variable
echo $MY_VAR
```

---

## 17. Red Hat Kickstart
Automating system installation using Kickstart.

### Example:
```bash
# Generate a Kickstart file
anaconda-ks.cfg

# Start a Kickstart installation
sudo ksvalidator /path/to/kickstart.cfg
```

---

## 18. SELinux Basics
Security-Enhanced Linux (SELinux) basics.

### Example:
```bash
# Check SELinux status
sestatus

# Change SELinux mode
sudo setenforce 0  # Permissive mode
sudo setenforce 1  # Enforcing mode
```

---

## 19. Firewall Management with firewalld
Managing the firewall using firewalld.

### Example:
```bash
# Start and enable firewalld
sudo systemctl start firewalld
sudo systemctl enable firewalld

# Allow HTTP traffic
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload
```

---

## 20. Network Time Protocol (NTP)
Configuring time synchronization.

### Example:
```bash
# Install NTP
sudo dnf install chrony

# Start and enable the service
sudo systemctl start chronyd
sudo systemctl enable chronyd

# Check synchronization status
chronyc tracking
```

---



---

## 21. Log Management with journalctl
Managing system logs using journalctl.

### Example:
```bash
# View the latest logs
journalctl -xe

# View logs for a specific service
journalctl -u sshd

# Clear logs
sudo journalctl --vacuum-time=1d
```

---

## 22. Backup and Restore
Creating and restoring system backups.

### Example:
```bash
# Create a tar backup
tar -cvzf backup.tar.gz /important/data

# Restore from backup
tar -xvzf backup.tar.gz -C /restore/location
```

---

## 23. Troubleshooting Boot Issues
Debugging boot problems.

### Example:
```bash
# Check the boot log
journalctl -b

# View GRUB boot menu
sudo grub2-editenv list
```

---

## 24. Kernel Management
Updating and managing the Linux kernel.

### Example:
```bash
# List installed kernels
rpm -q kernel

# Install a new kernel
sudo dnf install kernel

# Remove an old kernel
sudo dnf remove kernel-old-version
```

---

## 25. Network Bonding and Teaming
Configuring network bonding for redundancy.

### Example:
```bash
# Create a bond interface
nmcli con add type bond ifname bond0 mode active-backup

# Add slaves to the bond
nmcli con add type ethernet ifname eth1 master bond0
nmcli con add type ethernet ifname eth2 master bond0
```

---

## 26. Advanced Shell Scripting
Writing advanced shell scripts.

### Example:
```bash
#!/bin/bash

# Check disk space and alert if usage is over 90%
df -h | awk '$5 > 90 {print "Disk space alert:", $5}'
```

---

## 27. Ansible Basics
Automating tasks using Ansible.

### Example:
```bash
# Create an inventory file
echo "[servers] 
192.168.1.100" > inventory

# Run an Ansible command
ansible -i inventory servers -m ping
```

---

## 28. Containerization with Podman
Using Podman for container management.

### Example:
```bash
# Run a container
podman run -d --name webserver -p 80:80 nginx

# List running containers
podman ps

# Stop and remove a container
podman stop webserver
podman rm webserver
```

---

## 29. Web Server Management (Apache/Nginx)
Setting up and managing a web server.

### Example:
```bash
# Install Apache
sudo dnf install httpd

# Start and enable Apache
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

## 30. Database Management (MariaDB/PostgreSQL)
Setting up a database server.

### Example:
```bash
# Install MariaDB
sudo dnf install mariadb-server

# Start and enable the service
sudo systemctl start mariadb
sudo systemctl enable mariadb

# Secure MariaDB
sudo mysql_secure_installation
```

---

---

## 31. Email Server Configuration
Setting up an email server using Postfix.

### Example:
```bash
# Install Postfix
sudo dnf install postfix

# Start and enable Postfix
sudo systemctl start postfix
sudo systemctl enable postfix

# Check Postfix status
systemctl status postfix
```

---

## 32. DNS Server Configuration
Setting up a DNS server using BIND.

### Example:
```bash
# Install BIND
sudo dnf install bind bind-utils

# Start and enable BIND
sudo systemctl start named
sudo systemctl enable named

# Check BIND status
systemctl status named
```

---

## 33. DHCP Server Configuration
Configuring a DHCP server to assign IP addresses.

### Example:
```bash
# Install DHCP server
sudo dnf install dhcp-server

# Edit DHCP configuration file
sudo nano /etc/dhcp/dhcpd.conf

# Start and enable DHCP service
sudo systemctl start dhcpd
sudo systemctl enable dhcpd
```

---

## 34. NFS and Samba File Sharing
Setting up file sharing using NFS and Samba.

### Example (NFS):
```bash
# Install NFS server
sudo dnf install nfs-utils

# Start and enable NFS service
sudo systemctl start nfs-server
sudo systemctl enable nfs-server

# Export a directory
echo "/shared 192.168.1.0/24(rw,no_root_squash)" | sudo tee -a /etc/exports

# Apply export changes
sudo exportfs -arv
```

### Example (Samba):
```bash
# Install Samba
sudo dnf install samba

# Start and enable Samba
sudo systemctl start smb
sudo systemctl enable smb
```

---

## 35. Advanced SELinux Configuration
Fine-tuning SELinux policies.

### Example:
```bash
# List SELinux booleans
getsebool -a

# Set a SELinux boolean value
sudo setsebool -P httpd_can_network_connect on

# Change SELinux file context
sudo chcon -t httpd_sys_content_t /var/www/html -R
```

---

## 36. System Security and Hardening
Implementing security best practices.

### Example:
```bash
# Disable root login via SSH
sudo sed -i 's/^PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
sudo systemctl restart sshd

# Enable automatic security updates
sudo dnf install dnf-automatic
sudo systemctl enable --now dnf-automatic.timer
```

---

## 37. Performance Monitoring and Tuning
Optimizing system performance.

### Example:
```bash
# Monitor system performance
top

# Check CPU and memory usage
vmstat 1 5

# Analyze disk usage
iostat -x 1 5
```

---

## 38. Disaster Recovery Planning
Planning and implementing disaster recovery.

### Example:
```bash
# Create a backup of critical files
tar -czvf /backup/important_files.tar.gz /etc /home /var

# Restore from backup
tar -xzvf /backup/important_files.tar.gz -C /restore/location
```

---

## 39. High Availability with Pacemaker
Setting up high availability clustering.

### Example:
```bash
# Install Pacemaker
sudo dnf install pacemaker corosync

# Start and enable services
sudo systemctl start pacemaker
sudo systemctl enable pacemaker

# Check cluster status
pcs status
```

---

## 40. Load Balancing with HAProxy
Configuring HAProxy for load balancing.

### Example:
```bash
# Install HAProxy
sudo dnf install haproxy

# Start and enable HAProxy
sudo systemctl start haproxy
sudo systemctl enable haproxy

# Edit HAProxy config file
sudo nano /etc/haproxy/haproxy.cfg
```

---

---

## 41. Virtualization with KVM
Setting up and managing virtual machines using KVM.

### Example:
```bash
# Install KVM and dependencies
sudo dnf install qemu-kvm libvirt virt-install bridge-utils

# Start and enable libvirt service
sudo systemctl start libvirtd
sudo systemctl enable libvirtd

# List active virtual machines
virsh list --all
```

---

## 42. Cloud Integration with OpenStack
Integrating Red Hat with OpenStack for cloud deployments.

### Example:
```bash
# Install OpenStack client
sudo dnf install python3-openstackclient

# Authenticate with OpenStack
source openrc.sh

# List available instances
openstack server list
```

---

## 43. Advanced Networking (VLANs, VPNs)
Configuring VLANs and VPNs for advanced networking.

### Example (VLAN):
```bash
# Create a VLAN interface
sudo nmcli connection add type vlan ifname eth0.100 dev eth0 id 100

# Assign an IP address to the VLAN
sudo nmcli connection modify eth0.100 ipv4.addresses 192.168.100.1/24
sudo nmcli connection up eth0.100
```

### Example (VPN):
```bash
# Install OpenVPN
sudo dnf install openvpn

# Start OpenVPN service
sudo systemctl start openvpn-server@server
sudo systemctl enable openvpn-server@server
```

---

## 44. Automation with Puppet
Using Puppet for configuration management.

### Example:
```bash
# Install Puppet agent
sudo dnf install puppet-agent

# Start Puppet service
sudo systemctl start puppet
sudo systemctl enable puppet

# Apply a Puppet manifest
puppet apply -e 'file { "/tmp/testfile": ensure => present, mode => "0644" }'
```

---

## 45. Advanced Log Analysis
Analyzing system logs for troubleshooting.

### Example:
```bash
# Search for errors in logs
journalctl -p err

# Monitor logs in real-time
tail -f /var/log/messages

# Analyze logs with awk
awk '/error/ {print $0}' /var/log/syslog
```

---

(End of document)

---

## 1. Introduction to Linux
Linux is an open-source operating system that powers servers, desktops, and embedded systems.

### Examples:
```bash
# Check the Linux version
cat /etc/os-release

# Check system uptime
uptime

# View system information
uname -a
```

---

## 2. File System Hierarchy
Understanding the Linux directory structure.

### Examples:
```bash
# List root directories
ls /

# View disk usage of directories
du -sh /*

# Find the location of a binary
which bash
```

---

## 3. Basic Linux Commands
Essential commands for navigating and managing Linux.

### Examples:
```bash
# Display current directory
pwd

# List files in a directory with details
ls -lah

# Create and delete directories
mkdir test_dir
rmdir test_dir

# Copy and move files
cp file1.txt file2.txt
mv file1.txt new_location/

# Display file contents
cat file.txt

# Search for a word in a file
grep "word" file.txt
```

---

## 4. User and Group Management
Managing users and groups in Linux.

### Examples:
```bash
# Add a new user
sudo useradd alice

# Set user password
sudo passwd alice

# Create a new group
sudo groupadd developers

# Add a user to a group
sudo usermod -aG developers alice

# View all groups a user belongs to
groups alice

# Delete a user
sudo userdel alice

# Delete a group
sudo groupdel developers
```

---

## 5. File Permissions and Ownership
Understanding file permissions and managing them.

### Examples:
```bash
# View file permissions
ls -l myfile.txt

# Change file permissions (Owner can read, write, execute; others can only read)
chmod 755 myfile.txt

# Change file ownership
chown alice:developers myfile.txt

# Give execute permission to all users
chmod +x script.sh

# Remove write permission for group
chmod g-w file.txt
```

---

## 6. Package Management with YUM/DNF
Installing and managing software packages.

### Examples:
```bash
# Install a package
sudo dnf install httpd

# Remove a package
sudo dnf remove httpd

# List installed packages
dnf list installed

# Search for a package
dnf search nginx

# Update all packages
sudo dnf update -y
```

---

## 7. System Services and systemctl
Managing system services with systemctl.

### Examples:
```bash
# Start a service
sudo systemctl start httpd

# Stop a service
sudo systemctl stop httpd

# Restart a service
sudo systemctl restart httpd

# Enable a service to start at boot
sudo systemctl enable httpd

# Check the status of a service
sudo systemctl status httpd

# Disable a service
sudo systemctl disable httpd
```

---

## 8. Networking Basics
Configuring and managing network settings.

### Examples:
```bash
# Display network interfaces
ip a

# Assign an IP address
sudo ip addr add 192.168.1.100/24 dev eth0

# Display network routes
ip route show

# Check connectivity to another machine
ping 8.8.8.8

# View DNS information
nslookup example.com
```

---

## 9. SSH and Remote Access
Configuring SSH for remote access.

### Examples:
```bash
# Connect to a remote server
ssh user@remote_host

# Copy files over SSH
scp file.txt user@remote_host:/home/user/

# Generate an SSH key pair
ssh-keygen -t rsa -b 4096

# Copy SSH public key to remote server for passwordless authentication
ssh-copy-id user@remote_host
```

---

## 10. Disk Partitioning and Management
Creating and managing disk partitions.

### Examples:
```bash
# View disk partitions
lsblk

# Create a new partition
fdisk /dev/sdb

# Format a partition with ext4
mkfs.ext4 /dev/sdb1

# Check disk usage
df -h

# Display information about disk partitions
fdisk -l
```

---

## 11. Logical Volume Management (LVM)
LVM provides flexible disk management.

### Examples:
```bash
# Create a physical volume
pvcreate /dev/sdb1

# Create a volume group
vgcreate my_vg /dev/sdb1

# Create a logical volume
lvcreate -L 10G -n my_lv my_vg

# Extend a logical volume
lvextend -L +5G /dev/my_vg/my_lv

# Resize the filesystem after extending LVM
resize2fs /dev/my_vg/my_lv
```

---

## 12. File System Creation and Mounting
Creating and mounting file systems.

### Examples:
```bash
# Create an ext4 file system
mkfs.ext4 /dev/sdb1

# Mount the partition
mount /dev/sdb1 /mnt

# View mounted filesystems
mount | grep /mnt

# Unmount the partition
umount /mnt

# Automatically mount a filesystem at boot (add entry to /etc/fstab)
echo "/dev/sdb1 /mnt ext4 defaults 0 0" >> /etc/fstab
```

---

## 13. Process Management
Managing system processes effectively.

### Examples:
```bash
# List running processes
ps aux

# Find a process by name
pgrep apache

# Kill a process by ID
kill -9 <PID>

# Monitor system resources in real time
top

# View detailed resource usage
htop
```

---

## 14. Cron Jobs and Automation
Automating tasks using cron jobs.

### Examples:
```bash
# Edit crontab for the current user
crontab -e

# Add a cron job to run a script every day at midnight
0 0 * * * /path/to/script.sh

# List all cron jobs for a user
crontab -l

# Remove all cron jobs for a user
crontab -r
```

---

## 15. Shell Scripting Basics
Writing basic shell scripts.

### Examples:
```bash
# Create a simple script
echo -e "#!/bin/bash\necho Hello, World!" > script.sh

# Make it executable
chmod +x script.sh

# Run the script
./script.sh

# Use variables in a script
echo -e "#!/bin/bash\nNAME='Alice'\necho Hello, $NAME" > script.sh
```

---
