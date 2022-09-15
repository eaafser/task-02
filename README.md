## k8s with Cluster 1 master 2 workers

>> Steps 1
- Create users in each node
- Install dependencies and containerd on each node
- Master node readyness
- Add worker nodes in k8s cluster


>> Step 2

Follow below steps for run Ansible
hosts.yml - Node details  
non-root-user.yml - Create system user information
kube-dependencies.yml - Install packages in nodes.
master-cluster.yml - Configure master node and install flannel CNI
worker-cluster.yml - For join worker nodes

>> Step 3

$ ansible-playbook -i hosts users.yml

$ ansible-playbook -i hosts non-root-user.yml

$ ansible-playbook -i hosts kube-dependencies.yml

$ ansible-playbook -i hosts master-cluster.yml

$ ansible-playbook -i hosts worker-cluster.yml

Now k8s cluster is ready

>> Step 4

Introduce matrics service 

$ kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

>> Step 5

Install dashboard

$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.5.0/aio/deploy/recommended.yaml


