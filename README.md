# ICW Example playbooks

handy commands:

ansible-builder build --tag hostname/infra_automation_ansible29

podman image prune

podman run -it quay.io/danielgoosen/vo-ee2 /bin/bash

pip freeze

ansible galaxy collection list

podman run 4fb8363c0cdc ansible-galaxy collection list

podman run 4fb8363c0cdc pip3 list

podman login https://aap2pah.rydzinski.local --tls-verify=false

podman push aap2pah.rydzinski.local/demo_ee --tls-verify=false
