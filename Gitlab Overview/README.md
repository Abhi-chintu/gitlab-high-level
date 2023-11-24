# Configuring GitLab self-runner on EC2 

Pre-Requisite

	AWS account
	EC2 instance

If your using Linux operating system in AWS
1. Goto setting --> CICD --> Runners
<img width="339" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/7211e5e9-2fb1-479d-865a-7f2ecb2a0255">

2. Click on new Runner options and follow the installation command given asper your operating system
<img width="360" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/149dafba-7bd4-4b8f-a6e1-5f57d293aaa7">

3. After running the command on the ec2 instance. It will ask for Runner config provide the details as given below.
<img width="408" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/15b0499d-b23a-43d0-8910-4fda7a2c2040">

4. Now you can see the new runner in the UI
<img width="325" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/98893076-c5f0-43f8-aa4b-0541caa295cd">

# Gitlab Docker registry
<img width="394" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/a1aa87bf-aaf1-4767-86c8-dbc60d859d43">

- Package Registry = Use Gitlab as private or public registry for variety of supported package managers like Maven, npm, etc...
- Container Registry = Registry to store Docker images, were we push the docker images .

# Before building the image 
1. Add User to Docker Group:
   
		sudo usermod -aG docker $USER


2. Restart Docker and CI Runner:

		 sudo service docker restart
		 sudo gitlab-runner restart






