# interview-challenge-terraform
Interview Challenge to provision resources using Terraform

# Objective

1. Create a Python script to fetch data from an API
1. Create the resources on OCI as using Terraform
1. Configure and deploy the Python script on the created instance using Ansible
1. Create Ansible roles and playbooks to perform tasks

# Python

1. Install python dependencies requests
1. Under python directory, modify `app.py` to fetch data from url `https://dummyjson.com/products?skip=5&limit=100` and write the data to an output file `data.json`

# Terraform

1. Refer file `Steps to Access Oracle Cloud.md` to ensure you can login to Oracle Cloud
1. Create the resources as shown in the pdf file `demo-stack-terraform.pdf`
1. Use the below mentioned variables in your terraform code:
    - Compartment ID : `ocid1.compartment.oc1..aaaaaaaau2d5tlzxsvkpz3iuzhuo4uemcn7kzmkv6fhjqbpxdzpg5ijz4tqq`
    - Image ID : `ocid1.image.oc1.iad.aaaaaaaab3w3vzjenuyy3idksenczspj77wz74o7unpxid6xr7zmsyi7u47q`
    - Shape : `VM.Standard.E4.Flex`
    - Availability Domain : `KGRc:US-ASHBURN-AD-1`
1. Modify public compute instance metadata to add your ssh public key and also add public key below for grading purposes
    > ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC65bld2dmUibITLdPl9GQpHkFyHLOp8VwwyiPUT9qYOOopyW2i/EfsZeINsZSBXKpoS4dpfr9zXbR7M4QJHomhUhd9Wbpoo7fi1wfCUYYP7pL4w74ZZDVKLMoXdBvYsg1udR//efxyOlEyLd6R/Td4nSAjhwalLf9uE4uRX2+eKxPDFyY/AGALT7qiHsqp7tNQ0OvuL0CIN/z+wxBVr2zN+HFp9XPfF9cF31xBFQiRYtXHo2c0brgsJ2zNNiAKet8GOmY0djel9VEemnviRmEsVrgW+Q3upA02BtNNQZt50/mgfNLtY3aaRdB8OZ+yr9YLGQKW8hvhKOu/rbzgUYs1 rbhagat@AJTV3VGQF2.local
1. Create `output.tf` to output public_ip of compute instance
1. Create a modules of the different resources that you are using. Grading will also be done based on how modularised and reusable your code is.


# Ansible

Before beginning ansible section, checkin python code to repo
1. Under ansible directory, create a role to:
    1. Install python dependencies
    1. Create a directory `/app/`
    1. Copy the python code in the directory.
    1. Run the code and create the `data.json` in the `/app` directory
1. Create a role to:
    1. Read the file `data.json`
    1. Take keyword to search as input
    1. Search for the keyword in the `description` tag. If it matches perfectly or is a subtring of the word, then output the `title`.
1. Create a single playbook to execute the above mentioned tasks 

# Comments/implemention details/thought process
Feel free to add any comments or details here that would be useful when grading your solution. If you face any issues and you need to make an assumptions or any other step to proceed, please document them.


# Grading Process

1. Under terraform directory, run terraform to create infrastructure
    - terraform init
    - terraform apply
1. Under ansible directory, run ansible-playbook to install hello world app, create firewalld rules, and start app
    - ansible-playbook -i <compute_ip>, playbook.yml --private-key ~/.ssh/id_rsa -u opc
1. Navigate browser to http://\<public_ip\>:5000 to show hello world app is running
1. Reboot compute instance
1. Verify app starts automatically and refresh browser
1. SSH into compute instance to show public_key is working
1. Ping VM in private subnet B to check if connectivity is setup correctly
1. Ping VM in private subnet A should fail since no route exists