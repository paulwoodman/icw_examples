# ICW Example playbooks

# How to Build a Custom Execution Environment for AAP

On a RHEL 8 or 9 OS

# install package for a virtual env
1. sudo dnf install python3.11 -y

# Create a virtual enviroment call ansible-venv
2. python3.11 -m venv ansible-venv

# Activate the virtual environment
3. source ansible-venv/bin/activate

# Install the required packages to build an Execution environment in the VENV
4. pip3 install ansible ansible-builder ansible-navigator

#  Log into registry.redhat.io so you can pull a Red Hat container image for the build
5.  podman login registry.redhat.io

# Create a folder to build your EE
5. mkdir test_ee

# To kept the initial build simple we will use 1 file. galaxy collection and python modules can be added in sperrate requirement files to make it easier to read. See examples
6. vi execution-environment.yml

# In the file in the baseline items for a EE build

version: 3


images:
  base_image:
    name: registry.redhat.io/ansible-automation-platform-24/ee-minimal-rhel8:latest

dependencies:
  galaxy:
    collections:
      - community.vmware
  python:
      - pytest

options:
  package_manager_path: /usr/bin/microdnf

# Build the container image and use tags to help easily define what the EE includes
7. ansible-builder build --tag vmaware_ee

#. Once the build completes you can verify the image in podman
8. podman images


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

podman rmi image_name
