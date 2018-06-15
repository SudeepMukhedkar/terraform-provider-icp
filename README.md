# Terraform Basic_Sub_Module

This is the module for deployment of IBM cloud Private-CE 2.1.0 . Using this sub_module one can deploy IBM Cloud Private-CE 2.1.0 in [Basic topology][1].

[1]: https://www.ibm.com/developerworks/community/blogs/5092bd93-e659-4f89-8de2-a7ac980487f0/entry/Availability_considerations_for_single_ICP_cluster_topologies?lang=en

# Prerequisites

For icp cluster deployment, It needs [ssh-key-value](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1604), number of worker nodes and path of image in main.tf 

## For configuration of cloud-init required steps

- cat your public key  
- past your public key(.pub)at <paste_your_public_key_here> in /node_config/master_config , /node_config/worker_config & /node_config/extraworker_config files

## Inputs( Edit is partially done)
| Variable           | Default       |Required| Description                            |File Location
|--------------------|---------------|--------|----------------------------------------|--------
|default_worker      |1              |Yes    |Number of default worker count|main.tf
|extra_worker          | 0              |Optional*     |Number of extra worker nodes count  |main.tf
|master_img_path          |            |Yes     |Path of the image for master node | main.tf
|worker_img_path          |            |Yes     |Path of the image for worker node | main.tf
|ssh_private_key_path          |  Path of SSH private key pair|Yes |Using this key you can log into created cluster nodes  |main.tf
|ssh_public_key_path          |  Path of SSH public key pair|Yes  |This key for password-less authentication with private key |main.tf


# IBM Cloud Private Cluster Configuration

If One wants other configuration instead of default configuration(like cluster_password,cluster_name), you can edit [config.yaml][2] file which is present in "scripts" folder. 

[2]: https://www.ibm.com/support/knowledgecenter/SSBS6K_2.1.0/installing/config_yaml.html

# To add extra worker node to Existing Cluster

After installing IBM cloud Private-CE 2.1.0, edit "main.tf" add count for extra worker nodes. After that do "terraform apply" .

# Troubleshooting
If ICP private installation fails, refer [Troubleshooting][5] of ICP

[5]: https://www.ibm.com/support/knowledgecenter/en/SSBS6K_2.1.0/troubleshoot/troubleshoot.html

