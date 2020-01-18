Expected Results:
Ansible being able to run locally without the need to have ssh installed.

Actual Results:
Ansible doesn't require ssh when ansible_connection=local is defined in the hosts file.
Ansible requires ssh for a playbook when run with flag --connection=local.
Ansible requires ssh for a playbook when declared connection: local in the playbook.
