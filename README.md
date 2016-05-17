# Jenkins_Demo
- hosts: all
  remote_user: ubuntu
  tasks:
   - name: Copy ansible inventory file to client
     copy: src=/etc/ansible/hosts dest=/home/ubuntu
     notify:
     - restart apache
   - name: ensure apache is running (and enable it at boot)
     service: name=apache2 state=started enabled=yes
  handlers:
    - name: restart apache
      service: name=apache2 state=restarted
