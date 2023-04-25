### In Vagrant language, Virtual machines are called boxes.
### A Vagrantfile is a file to describe the type of machine required for a project, and how to configure and provision that machine.

You specify a box environment and operating configurations in your Vagrantfile. You can use a box on any supported platform to bring up identical working environments. To enable teams to use and manage the same boxes, versions are supported.

### Note: Boxes require a provider, a virtualization product, to operate. Before you can use a box, ensure that you have properly installed a supported "provider" ( VirtualBox, Hyper-V, VMware and Docker).


The quickest way to get started is to select a pre-defined box environment from the publicly available catalog on Vagrant Cloud. You can also add and share your own customized boxes on Vagrant Cloud.

The vagrant box CLI utility provides all the functionality for box management. You can read the documentation on the vagrant box command for more information.


# Discover boxes

To find boxes, explore the public Vagrant box catalog for a box that matches your use case. The catalog contains most major operating systems as bases, as well as specialized boxes to get you started with common configurations such as LAMP stacks, Ruby, and Python.

The boxes on the public catalog work with many different providers. The list of supported providers is located in the box descriptions.


# Add a box
You can add a box from the public catalog at any time. The box's description includes instructions on how to add it to an existing Vagrantfile or initiate it as a new environment on the command-line.

A common misconception is that a namespace like "ubuntu" represents the official space for Ubuntu boxes. This is untrue. Namespaces on Vagrant Cloud behave very similarly to namespaces on GitHub. Just as GitHub's support team is unable to assist with issues in someone's repository, HashiCorp's support team is unable to assist with third-party published boxes.


# Official boxes
There are only two officially-recommended box sets.

HashiCorp publishes a basic Ubuntu 18.04 64-bit box that is available for minimal use cases. It is highly optimized, small in size, and includes support for VirtualBox, Hyper-V, and VMware.


__________________________________________________________________________________

To get started, create a folder where you'll host your box
### mkdir folder_name
________________________________________________________________________________

use the init command to initialize your environment.
### "vagrant init ubuntu/bionic64"
___________________________________________________________________________________

If you have an existing Vagrantfile, add hashicorp/bionic64.
### Vagrant.configure("2") do |config|
###   config.vm.box = "ubuntu/bionic64"
### end
_____________________________________________________________________________________

### Type "vim vagrantfile" to edit the file (the goal is to uncomment the line of the IP address and make sure you set up an available Ip adress, also uncomment the line of the network card).
_________________________________________________________________________________________

### Do "vagrant up" to provision the VM
________________________________________________________________________________________

In the case you provisioned without editing the vagrant file, edit your vagrantfile first
### Then do "vagrant reload --provision" to restart the virtual machine and force provisioning






===========================================================================================
# Vagrant Comand Cheat Sheet
===========================================================================================

# Creating a VM
- vagrant init — Initialize Vagrant with a Vagrantfile and ./.vagrant directory, using no specified base image. Before you can do vagrant up, you’ll need to specify a base image in the Vagrantfile.
- vagrant init <boxpath> — Initialize Vagrant with a specific box. To find a box, go to the public Vagrant box catalog. When you find one you like, just replace its name with box path. For example, vagrant init ubuntu/trusty64.

# Starting a VM
- vagrant up - starts vagrant environment (also provisions only on the FIRST vagrant up)
- vagrant resume — resume a suspended machine (vagrant up works just fine for this as well)
- vagrant provision — forces reprovisioning of the vagrant machine
- vagrant reload — restarts the Vagrant machine, loads new Vagrantfile configuration
- vagrant reload --provision — restart the virtual machine and force provisioning

# Getting into a VM
- vagrant ssh — connects to the machine via SSH
- vagrant ssh <boxname> — If you give your box a name in your Vagrantfile, you can ssh into it with the box name. Works from any directory.

# Stopping a VM
- vagrant halt — stops the vagrant machine
- vagrant suspend — suspends a virtual machine (remembers state)

# Cleaning Up a VM
- vagrant destroy — stops and deletes all traces of the vagrant machine
- vagrant destroy -f — same as above, without confirmation

# Boxes
- vagrant box list — see a list of all installed boxes on your computer
- vagrant box add <name> <url> — download a box image to your computer
- vagrant box outdated — check for updates vagrant box update
- vagrant boxes remove <name> — deletes a box from the machine
- vagrant package — packages a running VirtualBox env in a reusable box

# Saving Progress
- vagrant snapshot save [options] [vm-name] <name> — vm-name is often default. Allows us to save so that we can rollback at a later time

# Tips
- vagrant -v — get the vagrant version
- vagrant status — outputs status of the vagrant machine
- vagrant global-status — outputs status of all vagrant machines
- vagrant global-status --prune — same as above, but prunes invalid entries
- vagrant provision --debug — use the debug flag to increase the verbosity of the output
- vagrant push — yes, vagrant can be configured to deploy code!
- vagrant up --provision | tee provision.log — Runs vagrant up, forces provisioning, and logs all output to a file







