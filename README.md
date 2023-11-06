# GITLAB

Benefits of using Gitlab CI/CD
------------------------------
- Seamless integration into code repository  --> where as in Jenkins only CI/CD tool
- Using CI/CD wihtout overhead of setting it up yourself --> were as in Jenkins self-hosting is the only option
- Pipeline configuration as part of your application code
- Self-hosted or SaaS(managed)

Gitlab Architecture:
---------------------
- Gitlab has gitlab instance/gitlab server which host our application code and pipeline configuration.
- In connected to gitlab server it has Gitlab runners
	- were it acts like agent that run our CI/CD jobs.
	- Gitlab Server assigns pipeline jobs to available Runners.

Create Job in gitlab:
---------------------
<img width="591" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/73fec4ce-e11c-424b-9fb0-0314f92b677a">

Where or on which environment is the job executed?
--------------------------------------------------
 - pipeline jobs are executed on gitlab runner 
 - Where gitlab runners are executable on different OS
	- that what we call shell exeucutors
	- Commands are executed on OS
	- On the shell of the server, where Gitlab Runners is installed 
 - Docker conatainer
	- How we execute the job in linux machine for example by similar way we execute in 
	   docker containers.
	- Gitlab managed runner use Docker conatainer
	- So, our jobs are executed in Docker containers
   
Which Docker image is used?
---------------------------
- What image we use to run that container will be created. For example if we use mysql image then  
  mysql container is created.
- By default: gitlab managed Runners use a Ruby image to start the container.
