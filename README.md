# Setting-Up-AWS-EC2-Instance-For-Docker
OBJECTIVE:
Understand how to provision and configure an AWSEC2 instance suitable for docker deployments.
1. Launch an EC2 instance
2.SSH into the instance
3. Install docker on EC2 instance

## Steps

1. **Launch an EC2 instance**
   - Log in to your AWS Management Console.
   - Navigate to the EC2 dashboard.
   - Click on "Launch Instance" to start the instance creation wizard.
   - Select an Amazon Machine Image (AMI), instance type, configure instance details, add storage, configure security groups, and review the instance launch.
   - Finally, launch the instance.

2. **SSH into the instance**
   - Once the instance is launched, obtain its public IP address.
   - Open your terminal or SSH client.
   - Use the SSH command to connect to your EC2 instance:
     ```
     ssh -i your-key.pem ec2-user@your-instance-public-ip
     -----
   Replace `your-key.pem` with the path to your private key and `your-instance-public-ip` with the public IP address of your EC2 instance.

3. **Install Docker on EC2 instance**
   - Update the package index on the EC2 instance:
     ```
     sudo yum update -y
     ```
   - Install Docker:
     ```
     sudo amazon-linux-extras install docker
     ```
   - Start the Docker service:
     ```
     sudo service docker start
     ```
   - Add the `ec2-user` to the `docker` group to run Docker commands without sudo:
     ```
     sudo usermod -a -G docker ec2-user
     ```
   - Log out and log back in to apply the changes.
   - Verify Docker installation:
     ```
     docker --version
     ```

That's it! You've now set up an AWS EC2 instance for Docker deployments. You can now proceed with deploying and managing your Docker containers on this instance.
