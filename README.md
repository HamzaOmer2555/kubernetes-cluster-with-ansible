# kubernetes-cluster-with-ansible
This is a repository for setting up a Kubernetes cluster using Kubeadm on Debian Linux. 


# Pre-Requisistes

    - Ensure you have provisioned vms for control-plane and worker-plane.
    - Ensure connectivity between your machines through /etc/hosts
    - Ensure internet connectivity on all machines

# Instructions To Use This Repository

    1. git clone https://github.com/HamzaOmer2555/kubernetes-cluster-with-ansible.git

    2. Change the hostnames of the machines in the debian/hosts file.

    3. Change the values of master node ip address and cidr in debian/env_variables

    4. Ensure passwordless ssh from master to worker nodes

    5. Clear the previous environment if cluster was already initialized (or partial installation)
        
        * ansible-playbook clear_k8s_setup.yml --become -K

    6. Run the playbooks in the following order:

        * ansible-playbook setup_kubernetes.yml --become -K

        * ansible-playbook join_cluster_workers.yml --become -K

    7. Verify that the cluster is setup on master node

        * kubectl get nodes


# Details about the environment files in this repo


    ansible.cfg - Ansible configuration file created locally.

    hosts - Ansible Inventory File

    env_variables - Main environment variable file where we have to specify based on our environment.

    setup_kubernetes.yml - Ansible Playbook to perform prerequisites ready, setting up nodes, configure master node.

    join_cluster_workers.yml - Ansible Playbook to join worker nodes with master node.

    clear_k8s_setup.yml - Ansible Playbook helps to delete entire configurations from all nodes.

    playbooks - Its a directory holds all playbooks.