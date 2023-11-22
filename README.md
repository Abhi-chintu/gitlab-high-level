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
------------------------------------------------------------------------------------------------------------
# Basic excution of pipeline
 <img width="232" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/2e93f76d-c3ba-4065-b82d-3505a989fa95">

 -----------------------------------------------------------------------------------------------------------------------------------------
 
 # Stages Group Job
 <img width="338" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/74ae87e4-b90d-4a6a-8bd6-8cd0ebac0ed4">
 
-----------------------------------------------------------------------------------------------------------------------------------------

# Needs Dependency between Jobs
Consider there are many stages in the pipeline but we need to stop the pipeline in such a stage were if one of the stages fail.

<img width="396" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/97509085-8df1-4a97-b0e3-2017862e64eb">

In above image, at the build stage there is a error in the pipeline script and in the next stage we have given the annotation as **needs**

-----------------------------------------------------------------------------------------------------------------------------------------------
# "only" When we need to run the specific job in the pipeline
When we have to run the specific job, we use **only** and specify the branch name. Consider we have different branch in our repositary
and the stages we are building should effect the main branch, in such cases we use this method.

<img width="399" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/98938eff-486e-4905-92d3-6dbda88246bb">

In above image, WKT in the first stage there is no **only** but in the other two stages we have only. So if we are running the pipeline in 
main branch all the stages will be passed when we are in other branch only particular stage will be passed.

- only --> defines when a job runs
- expect --> defines when a job does not run
---------------------------------------------------------------------------------------------------------------------------------------------
# Workflow Rules Control Pipeline behavior
Workflow rules can be used when there will commits pushed to any other branch the flow automatically igonres. Pipeline execution will be done 
only to the main branch. Instead of giving **only** to each and every stages we can define **workflow** with some conditions.

<img width="331" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/6db0de25-c27c-4525-9362-66893e3cdfec">

# What are Executors in GitLab

GitLab Runner implements a number of executors that can be used to run your builds in different environments.
GitLab Runner provides the following executors:

	SSH
	Shell
	Parallels
	VirtualBox
	Docker
	Docker Autoscaler (Beta)
	Docker Machine (auto-scaling)
	Kubernetes
	Instance (Beta)
	Custom
 # Job execution flow in Gitlab

 <img width="817" alt="image" src="https://github.com/Abhi-chintu/gitlab-high-level/assets/94033251/20f6081f-ad82-4164-b3fa-154b7f757d9a">

 1. Runner rquests new job from GitLab instance.
 2. Runner compiles and sends the job's payload to Executor.
 3. Executor clones sources or downloads artifacts from Gitlab instance.
 4. Executor returns job output and status to the Runner.
 5. Runner updates job output and status to Gitlab instance.

# Shared Runners on GitLab

1. By default, Gitlab uses one of its shared runners to run your CI/CD Jobs.
2. These shared runners are maintained by GitLab
3. Docker machine Executors are used for them.

# Specific Runners on Gitlab

These Runners are used for the specific project. Consider a organisation has different project teams and one team cannot share the runner with other so at that time these specific Runners are utilized.	

- These are self managed runners and maintained by users were create, update and configurations are done by users.
- First set up machine
- install gitlab runner program
- Connect to gitlab instance

To Configure Runner 
1. Install Runner on any machine such as laptop, server, or cloud. And you can install runner on Any operating system.
2. Register the gitlab runner on the gitlab server








 


