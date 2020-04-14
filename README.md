# Kubernetes Cluster Setup in Public Cloud Using Ansible Playbooks
Provides Ansible playbook to setup a K8s Cluster (1 Manager and N workers)

## Ansible Setup
### Installation
[Installation guide](https://docs.ansible.com/ansible/latest/installation_guide/index.html) for various OS

### Ansible Documentation 
Ansible documentation is located [here](https://docs.ansible.com/ansible/latest/user_guide/index.html)


## AWS Setup
We will setup a 3 node cluster with 1 Manager and 2 Worker nodes.

Ensure the Manager node has atleast 2 vCPU and 4 GiB RAM

#### Recommended AWS Instances:

AWS AMI: Ubuntu Server 18.04 LTS (HVM), SSD Volume Type

Manager Nodes: [t2.large](https://aws.amazon.com/ec2/instance-types/t2/)

Worker Nodes: [t2.micro](https://aws.amazon.com/ec2/instance-types/t2/)

## Steps to run Ansible Playbook for setting Cluster in AWS

Ansible playbook is located in ```aws``` folder

Add the AWS instances IPs and ssh key path to ```aws-hosts``` file

Run the following commands:

```
# check the ansible playbook syntax
ansible-playbook --syntax-check kubernetes-cluster-1W-2M.yaml -i aws-hosts

# run the playbook
ansible-playbook kubernetes-cluster-1W-2M.yaml -i aws-hosts
```

The join command for worker nodes to join the master node is in the cluster-join.txt created by ```kubeadm init``` command and is located in the home directory of your Master node


## Future Enhancements
1. Use ansible variables to pass the join command from Manager to Worker Nodes. This will eliminate the need for user to manually run the join command aftre ```kubeadm init```
2. Add playbooks for GCP, Azure and OCI

## License
[MIT](https://choosealicense.com/licenses/mit/)


