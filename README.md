megaclisas-status
=================

http://hwraid.le-vert.net/wiki/DebianPackages



ansible-playbook


---
- hosts: all
  remote_user: root
  become: true
  serial : 20
  ignore_errors: yes
  tasks:
    - name: copy rpm pkg
      copy:  src=./MegaCli-8.07.14-1.noarch.rpm  dest=/opt/

    - name: install pkg
      shell: rpm -ivh  /opt/MegaCli-8.07.14-1.noarch.rpm

    - name: Create a symbolic link
      file:
        src: /opt/MegaRAID/MegaCli/MegaCli64
        dest: /usr/bin/megacli
        state: link

    - name: copy script
      copy: src=./megaclisas-status dest=/usr/local/bin/   mode=755
