
# CentOS 8 Installation

## Prepare USB Installation Stick

1. Download ISO image: http://ftp.halifax.rwth-aachen.de/centos/8.0.1905/isos/x86_64/CentOS-8-x86_64-1905-dvd1.iso
2. Write ISO image to empty USB stick (e.g. with Rufus under Windows, using UEFI partitioning scheme)

## Install CentOS from USB stick

1. Attach USB installation stick to target
2. Boot CPU (e.g. F26L)
3. Enter Boot Menu, select UEFI boot from USB stick, then choose "Test this media & Install CentOS"
4. Wait for CentOS installation dialogue
5. Accept language US and proceed
6. Add German keyboard layout and move it to the top of the list to select it as the default
7. Change Date & Time to Europe/Berlin then adjust current date/time
8. Software selection:
    - Base Environment: Workstation
    - Add-Ons:
        - Development Tools
        - System Tools
9. Installation Destination:
    - Select destination disk and choose storage configuration "Custom"
    - On the next page: Click here to create them automatically
    - Switch all file systems from xfs to ext4
    - Example partitioning:
      - /home     : cl-home    5    GiB
      - /boot     : sda9    1024    MiB
      - /boot/efi : sda2      99    MiB
      - /         : cl-root   27    GiB
      - swap      : cl-swap    7.83 GiB
10. Network & Hostname:
    - Choose available Ethernet controller with link and enable it
    - Specify Host name (e.g. centos) or leave default
11. Click: Begin Installation
12. Set root password: men
13. Create user: men, password: men
14. After installation completed: Click Reboot
15. Enter Boot Menu and boot CentOS
16. Licensing: Accept license agreement
17. Click: Finish configuration
18. Update packages:
    `[root@centos ~]# yum upgrade`

## Basic CentOS Configuration (not to automate)

1. Add CentOS target to /etc/hosts of your dev-pc, e.g.:  
    `<ip-of-CentOS-target> mdis4lin`
2. Add personal ssh key from your dev-pc, e.g.:  
    `dpfeuffer@vm-manjaro:~> ssh-copy-id men@mdis4lin`  
    `dpfeuffer@vm-manjaro:~> ssh-copy-id root@mdis4lin`

## Automated CentOS Configuration with Ansible

Apply ansible playbook to target, e.g.:  
`dpfeuffer@vm-manjaro:~/work/repos/ansible/centos_mdis> ansible-playbook site.yml`
