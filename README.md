# ansible-nameserver-change

Ansible playbook for changing /etc/resolv.conf file
!! Also now can change windows dns !!

Currently supported Operating Systems:
- CentOS 7
- Ubuntu 18.04
- Windows 2003 or later

# USAGE

ansible-playbook change-nameserver.yml -i <inventory_file> --extra-vars "server1=<nameserver1> server2=<nameserver2>"

# A dry run example (CentOS 7)

ansible-playbook change-nameserver.yml -l <centos_hostname> -C -vvv --extra-vars "server1=193.192.98.8 server2=212.154.100.18" 

# A dry run example (Ubuntu 18.04)

ansible-playbook change-nameserver.yml -l <ubuntu_hostname> -C -vvv --extra-vars "dns1=193.192.98.8 dns2=212.154.100.18"

# A dry run example (Windows)

ansible-playbook change-nameserver.yml -l <windows_hostname> -C -vvv --extra-vars "dns1=193.192.98.8 dns2=212.154.100.18"
# NOTES

- Because Ubuntu 18.04 has cloud-init , the script will not change the resolv.conf file but modify the cloud-init config to change dns servers.
- Be careful for variable names. This script uses "server" for CentOS , "dns" for Ubuntu and Windows.

## Known Issues

- When giving a single dns to "Windows" server , win_dns module crashes. You should give 2 dns servers at the same time.
