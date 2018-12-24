- hosts: loc
  tasks:
    - name: Ansible lineinfile regexp example
      lineinfile:
        dest: /home/mdtutorials2/remote_server.txt
        regexp: '^DevOps'
        state: absent
