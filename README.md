Magic Mirror Ansible Role
=========
Ansible role for maintaining MagicMirror installations.

Reads the mm_modules variable to install modules and build config.js
Copies files in mm_copy to the magic mirror root directory.

Extends the work done by https://github.com/anlai/MagicMirror-Ansible

What this role does:
  Reads the Modules variable from your Magic Mirror's host_vars file
  Installs nodejs and npm, in case either is needed for a custom module installation.
  Clones any module repos needed
  Installs the modules required
  Creates the config.js to display them.

This role does not:
  Install the Magic Mirror application.  It merely maintains an existing Magic Mirror.
  Remove unused modules or files.

This repo includes:
  The magic_mirror role
  Example hosts_var file
  Example playbook

I started this when I got tired of manually rebuilding Magic Mirrors, and instead of creating a hand full of custom scripts.  An ansible role seemed like the right way to do this, since the goal is the same IT automation I use for other projects.

My workflow is:
  Grab the latest http://unofficialpi.org/Distros/MagicMirrorOS/ image
  Install it using the Raspberry Pi Imager https://www.raspberrypi.com/software/ so the networking and ssh keys are handled
  Boot the device and wait for the default Magic Mirror display to come up
  Ssh into the device to confirm keys are working, and manually run "sudo apt-get update" in case there are warnings or issues
  Add a "modules" variable to my host_vars/new_device_name with the desired information
  Run "ansible-playbook -i hosts magic_mirror.yml -l new_device_name

## Setup

Create a magicmirror group containing your Magic Mirror hosts.
Set mm_root, mm_modules, and optionally mm_copy for each host.  You can find two samples in examples/host_vars.
Copy examples/magic_mirror.yml to your playbooks directory.

### Deployment

Run the magic_mirror.yml playbook to update your Magic Mirror installations.
