Wazuh Installation Failure

Issue:
Wazuh dashboard failed during installation.

Cause:
50GB VM disk ran out of space during package extraction

Resolution:
Expanded Ubuntu VM disk from 50GB to 80GB.
Grew partition + LVM + filesystem to use the new space with the commands below:
    sudo growpart /dev/sda 3
    sudo pvresize /dev/sda3
    sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
    sudo resize2fs /dev/ubuntu-vg/ubuntu-lv