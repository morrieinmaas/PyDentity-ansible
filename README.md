# PyDentity-ansible

An ansible playbook to deploy [PyDentity](https://github.com/OpenMined/PyDentity) on a remote machine.

### Prerequisites

Running this repo, an ansible playbook, requires you to install ansible. This has been tested with ansible v2.10.7 on Python 3.8.5. It is recommended installing ansible within a python virtual environment. First create a virtual environment of your choice in the disred location by using the `virtualenv` command. Activate the environment using `source /path_to_virtualenv/bin/activate`. You can then install ansible using `pip install ansible==2.10.7`. If you're unfamiliar with ansible and ansible playbooks you might want to check out their docs or a blog post to figure out what is going on. In essence, a playbook provisions a remote (or even local) machine as defined per YAML files.

### The playbook

In the root of this repo you find a playbook (pydentity-playbook.yml). The comments in the top of the file should give you a good indiccation about how to run this playbook either with a user/password combination or by using a cryptographic key.

You will need you change your targets (the hosts) you want to run this against in the `hosts` file. Further, you will possibly want to change the variable in `vars/host_vars.yml` to fit your need. But you may also leave them as they are. Don't worry about the password being "password" as the playbook disables password login via ssh. So unless someone has your private cryptographic key (e.g. an RSA key) no one will be able to login to your remote machine. 

### Running it

Copy the desired command from the comments of the playbook into a shell and make sure you are in the root of the project. Change the variables such as the username and key file to your needs and run it. That's it. After successfully running through the playbook you will have a ready-to-go instance for the PyDentity repo. 

Note: You will no longer be able to login as root and only be able to ssh into the machine providing a key using the `-i` flag of the ssh CLI. 

### Why bother?
This is handy, because you might be on a machine other than the tested (by PyDentity) Ubuntu 20.04 LTS setup. Your machine might not even be running Linux or capable of running docker. This way you can get up and running in a reliable way (given you have internet access). 

### Recommendations
Depending on your local setup you can make use of the remote machone in different ways. 

1. If you are using VSCode install the Remote-SSH plugin. This will allow you to connect to the remote machine and get a feeling almost as if you were developing on localhost. Port forwarding comes out of the box. So, you can access the jupyter notebooks running on the remote boc in your browser on `localhost` without any faff. 
2. The PyCharm commercial version has a similar functionality and will allow you to do the same.
3. You can also manually setup port-forwarding and ssh connection to your local machine and use a texteditor of your choice.
4. There re possibly plugins for other IDEs that will allow you to do this, but I have not done any research into this.