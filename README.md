Project: Aruba switch backups and upgrades

Hosts:
- furnace-core = 10.20.99.1 = 6300M
- garage-ac    = 10.20.99.2 = 6100
- office-acc   = 10.20.99.3 = 6100

User for switch access:
- tberno-admin

Expected image files on image server:
- /opt/ansible/aruba-upgrades/files/ArubaOS-CX_6400-6300_10_13_1160.swi
- /opt/ansible/aruba-upgrades/files/ArubaOS-CX_6100-6000_10_13_1161.swi

Suggested run order:
1. ansible-playbook playbooks/backup_configs.yml
2. ansible-playbook playbooks/stage_images.yml
3. ansible-playbook playbooks/set_boot_secondary.yml
4. ansible-playbook playbooks/reboot_switches.yml

Or use:
- ansible-playbook playbooks/full_upgrade_no_reboot.yml
- then later run playbooks/reboot_switches.yml
