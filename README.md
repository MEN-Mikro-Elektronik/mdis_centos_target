Note: Use centos8 branch for CentOS 8! 

# CentOS 7 Installation

## Prepare USB Installation Stick

1. Download ISO image: http://centos.mirror.iphh.net/CentOS/7.5.1804/isos/x86_64/CentOS-7-x86_64-DVD-1804.iso
2. Verify checksum
3. Write ISO image to empty USB stick (e.g. with Win32 Disk Imager under Windows)

## Install CentOS from USB stick

1. Attach USB installation stick to target
2. Boot CPU (e.g. F26L)
3. Choose "Install CentOS 7"
4. Wait for CentOS installation dialogue
5. Accept language US and proceed
6. Change Date & Time to Europe/Berlin and adjust current date/time
7. Add German keyboard layout and set it as default
8. Software selection: Development and Creative Workstation with following Add-Ons
    - Development Tools
    - Platform Development
    Wait a few minutes until dependencies are calculated
9. Installation Destination:
    - Select destination disk and choose I will configure partitioning" -> Done
    - On the next page: Click here to create them automatically
    - Switch all file systems from xfs to ext4
    - Choose 30GiB for / and 30GiB for /home
10. Network & Hostname:
    - Choose available Ethernet controller with link and enable it
    - Specify Host name (e.g. mdis4lin) or leave default
11. Click: Begin Installation
12. Set root password: men
13. Create user: men, password: men
14. Click: Finish configuration
15. Enter UEFI Boot Menu and boot CentOS
16. Licensing: Accept license agreement
17. Click: Finish configuration

## Basic CentOS Configuration (not to automate)

1. Add CentOS target to /etc/hosts of your dev-pc, e.g.:  
    `<ip-of-CentOS-target> mdis4lin`
2. Add personal ssh key from your dev-pc, e.g.:  
    `dpfeuffer@vm-suse:~> ssh-copy-id men@mdis4lin`  
    `dpfeuffer@vm-suse:~> ssh-copy-id root@mdis4lin`

## Automated CentOS Configuration with Ansible

Apply ansible playbook to target, e.g.:  
`dpfeuffer@vm-suse:~/work/repos/ansible/centos_mdis> ansible-playbook site.yml`
