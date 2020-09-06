# kubeadm-kubernetes-cluster

this play book is thought to provide a simple kubernetes cluster for test.
It provides a lab environment to test applications in a real multi node cluster.
As requirement, you should have installed the AWS CLI, you should have access key in order to 
 provision EC2 instances, and Ansible on your machine. In order to run the playbook the command is very straightforward: 
 ```ansible-playbook playbook.yml ```  
 
 In order to configure tall the needed you should rename sample_key.yml in key.yml filling all the needed keys. let me explain how to do
 
 ```yaml

aws_access_key_id: it is the access key id of your IAM user with EC2 grant  
aws_secret_access_key: it is the secret key id of your IAM user with EC2 grant  
aws_region: it is the region id in which you want install your K8s cluster for instance eu-central-1

aws:
  ec2:
    master:
      instances: 1 the paly book support single master configuration
      name: it is the name provided to the instance making it simple to search in the AWS console
    worker:
      instances: it can be what ever you want as soon as it is a positive numebr for testing 2 or 3 is a good option
      name: it is the name provided to the instance making it simple to search in the AWS console
    instance_type: it describe the size of your instance for instance like t2.medium
    keypair: it is the name of aws keypair neede to ansible in roder to connect via ssh and configure the cluster for you
    zone: it is the availavility zone in which you want install the cluster an availability zone example can be eu-central-1b
    ami: it is the ami id you can get this id can be get from aws console during the lunch of an instance please pick an amazon linux 2 isntance ami 
    volume:
      size: 8
      type: gp2

  vpc:
    id: it is the vpc id in which you want to install the cluster it can be get from web console under VPC section
    subnet_id: it is the subnet id in which you want to install the cluster it can be get from web console under VPC section

ansible_ssh_private_key_file: it is the path to the key pair downloaded form AWS you can get one during an instance creation and reuse or create a new one on AWS web console
```  

The whole architecture in a picture:

[](k8s-lab.png)