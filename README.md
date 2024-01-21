# Magic Mirror Ansible Role

Welcome to the Magic Mirror Ansible Role, designed to streamline the maintenance of your MagicMirror installations. This role simplifies the process of managing your Magic Mirror setup, making it easier and more efficient.

## Features

**What this role does:**
- Install the Magic Mirror application if it is not found.
- Installs Node.js and npm, ensuring they are available for custom module installations.
- Reads the `mm_modules` variable from your Magic Mirror's `host_vars` file.
- Clones any module repositories needed.
- Installs the modules listed in the `mm_modules` variable.
- Copies files specified in `mm_copy` to the Magic Mirror root directory.
- Generates the `config.js` file.

**What this role does not do:**
- Install the Magic Mirror application itself. It is designed to maintain an existing Magic Mirror installation.
- Clean up unused modules or files.

## Repository Contents

This repository includes:
- The `magic_mirror` role.
- An example `host_vars` file.
- An example playbook.

## Setup

Here's how to set up and use this Ansible role for maintaining your Magic Mirror installations:

1. Clone this repository into your Ansible roles directory.

2. Create a group called `magicmirror` containing your Magic Mirror hosts.

3. Configure the following variables in each host's `host_vars` file:
   - `mm_root`: Magic Mirror root directory path.
   - `mm_modules`: List of modules to install.
   - `mm_copy` (optional): List of files to copy to the Magic Mirror root directory.

   You can refer to the examples in the `examples/host_vars` directory.

4. Copy `examples/magic_mirror.yml` to your playbooks directory.

## Deployment

To update your Magic Mirror installations, run the `magic_mirror.yml` playbook. This playbook will apply the necessary maintenance tasks to your Magic Mirrors based on the configured variables.

## Background

The inspiration for this role came from the need to automate and simplify the process of maintaining Magic Mirrors. Here's a brief overview of my workflow for deploying a Magic Mirror:

1. I start with the latest [MagicMirrorOS image](http://unofficialpi.org/Distros/MagicMirrorOS/) and use [Raspberry Pi Imager](https://www.raspberrypi.com/software/) for installation to handle networking and SSH keys.

2. Once the device is booted, I SSH into it to confirm key functionality and manually run `sudo apt-get update` to address any warnings or issues.

3. I add a `modules` variable to my `host_vars/new_device_name` file with the desired module information.

4. Finally, I run `ansible-playbook -i hosts magic_mirror.yml -l new_device_name` to apply the updates and configurations.

## Your Contribution

This role is designed to meet my specific needs, but I'm open to expanding its functionality to serve a broader audience. If you require additional features or have suggestions, please open an issue, and we can discuss potential improvements. Likewise, I welcome pull requests for fixes or enhancements that maintain the role's simplicity and efficiency. Thank you for considering the Magic Mirror Ansible Role for your Magic Mirror maintenance needs!