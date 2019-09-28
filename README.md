1.SYSTEM REQUIREMENT: 
 -CENT OS 7 minimal  ##CentOS-7-x86_64-Minimal-1810.iso
 -Use Root Credentials with default password as 123 
 -Requires two cloned centos VM:
  1. ansible-master
  2. appserver
 -Add ssh Fingerprint before execution. Just ssh into appserver and vice versa or generate your own shh key using ssh-keygen 


2.Edit the hosts and hostname file:
  1.  cat > /etc/hosts
      127.0.0.1   localhost ansible-master
      ::1         localhost ansible-master
  2. cat > /etc/hostname
      ansible-master
  3. Shutdown and restart system with following CMD- "shutdown now -r"

  4.same for Appserver just replace ansible-master with appserver.

3.Editing Inventory File:
  -replace the ip address in invertory file with your server IP.


4.Run following command:
  
  - ansible-playbook playbook.yml -i inventory.txt

It will install docker on server, enable the service, install docker-py, run mysql container with root user and password,and creates database my_wiki, and a media container on port 8080:80 which can be viewd on brower by using Hostip i.e 192.x.x.x:8080.

On media wiki in place of database host just use container name of mysql i.e "db" and use "root" as a password.

You may find bugs here and there, I am working in it.
