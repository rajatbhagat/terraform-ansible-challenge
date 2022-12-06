# interview-challenge-terraform
Interview Challenge to provision resources using Terraform

# Objective

1. Solve the programming challenge
1. Create the resources on OCI as using Terraform
1. Configure and deploy the programming challenge on the created instance using Ansible
1. Create Ansible roles and playbooks to perform tasks

# Programming Challenge

Write a program in Go / Node / Java / Python to:
1. Read the file named : `/programming/file1`
1. Sort the file on the IP address column
1. Make sure to find and remove duplicates programmatically.
1. Then generate a reverse name file with the records - see an example on how output should like for a single record in output-sample.
1. Write the output to : `outfile1`


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

Before beginning ansible section
1. Under ansible directory, create a role to:
    1. Configure the instance so that you are able to deploy and execute the programming challenge
    1. Deploy and run the code in this directory to generate the output file: `outfile1`
    1. Print the contents of the `outfile1` onto the console
1. Create a role to:
    1. Ping the instance created in the private subnet.
    1. Ping the instance and dump the output on the console.
1. Create a single playbook to execute the above mentioned roles
