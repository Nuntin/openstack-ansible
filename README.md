# openstack-ansible pike
1 Infrastructure Node
3 Compute Node
1 Storage Node


Howto
1.Config Interface Network

2.Prepare the deployment host all
  # apt-get update
  # apt-get dist-upgrade
  
  # apt-get install aptitude build-essential git ntp ntpdate \
  openssh-server python-dev sudo
  
  # apt-get install bridge-utils debootstrap ifenslave ifenslave-2.6 \
  lsof lvm2 ntp ntpdate openssh-server sudo tcpdump vlan
  
   # echo 'bonding' >> /etc/modules
   # echo '8021q' >> /etc/modules
   
 3.Configure SSH keys
   All Node sudo no password
   sudo -i
   # visudo
   # search %sudo
      devops  ALL:(ALL) NOPASSWD: ALL
   Permit Root Login   
   # vi /etc/ssh/sshd_config
    PermitRootLogin yes
   
   # systemctl restart sshd
   # ssh-keygen
   # ssh-copy-id root@xxx.xxx.xxx.xxx

 4.Install the source and dependencies
  # cd /opt
  # git clone project
  # cd openstack-ansible/scripts/
  # ./bootstrap-ansible.sh 
 
  
 5.Playbooks to install OpenStack
  # vi /etc/openstack_deploy/openstack_user_config.yml
  # openstack-ansible setup-hosts.yml --limit 'all:!log1'  
  # openstack-ansible setup-infrastructure.yml 
  # openstack-ansible setup-openstack.yml 
