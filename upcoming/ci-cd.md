# CI/CD

Quick description of what it is

Then just get into some of the key components of a generic build, test, deploy pipeline.

Chat about Github Actions features specifically and how I am now pretty comfortable with them.

- Reusable workflows.
- Set up of SSH keys (Deploy Keys in Github).
- Usage of docker image and interacting with docker registry or whatever it's called on AWS.

GitHub Actions
For some reason I found the thought of interacting with automated workflows in our CICD pipeline a little intimidating to begin with. However, once I got hands-on with it it all became pretty straightforward.
----
A workflow is a collection of jobs that are made up of steps with the possibility to leverage actions within each of these steps.
-------
Those are some of the GitHub specific terms. 
Actions can for a step in a job which come from the marketplace (or from other sources such as a git repo??) This is a little confusing since both the platform at the largest and one of its smallest components are called the same thing
GitHub has really good documentation for this, so I won’t go into too much detail on this.
Runners are where each job in a workflow is taking place and can be self-hosted or hosted by GitHub, need to actually check if there is any other options here. Can specify the OS to use if using GitHub and they also provide some free runner access to public repos I believe.
Services are docker containers for a particular runner completing a job. Since jobs run in parallel by default then it containers are specific to the job in question.
By default, these can run in parallel but control between dependent jobs can be enforced with the likes of the needs syntax of a workflow file which creates a dependency between jobs so it won't run until successful completion of the job that it needs.
The workflow syntax also includes inputs and outputs. Inputs can be defined for a workflow which provides access to these values using the input context. Needs is another example of a context which can provide access to data between dependent workflows. E.g the out put of a dependent job.
An example of this would be storing the docker image tag generated in the build workflow in the dependent deploy workflow. 
Github expressions can be used to interact with such contexts. Which is the dollar syntax you may see from time to time.
Concurrency group can be defined at the top of workflow which will ensure that only a single workflow or job is running at any one time. Flags can also be set to cancel in progress. E.g New build of uat cancels those in progress and runs another instance of that workflow.
Reusable workflows provide a means to dry up your pipelines across multiple projects. These can be stored in a central repository and called from other workflows within the organisation.

Link to 
-	How to set up self-hosted runners for Github actions



