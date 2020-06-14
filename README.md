**Integrating GitHub Branches with Jenkins & Docker**

Our main objective is to:

Job 1: If Developer pushes to dev branch then Jenkins will fetch from dev and deploy on dev-docker environment.

Job 2: If Developer pushes to master branch then Jenkins will fetch from master and deploy on master-docker environment. Both dev-docker and master-docker environment are on different docker containers.

Job 3: Manually the QA team will check (test) for the website running in dev-docker environment. If it is running fine then Jenkins will merge the dev branch to master branch

**Prerequisites:**

Linux and/or Windows 10 having Docker and Jenkins Installed
A reliable browser
Basic batch shell commands for either linux or powershell and for basic docker commands
A. First We Build Ourselves a Docker Image Containing Only httpd or Apache2

Using 'docker pull centos' we download the latest centos image
We need a docker file having the following lines

```FROM centos      #importing the image

MAINTAINER Kanae-San     #this is an optional step 

RUN yum install -y httpd     #installs httpd

EXPOSE 80    #exposes the image to post 80

ENTRYPOINT ["/usr/sbin/httpd", "-D", "FOREGROUND"]   #makes sure only httpd runs```

Then make sure your inside the directory where you have saved this Dockerfile (Dockerfile has no file format) and build your httpd image using
docker build -t myweb . 
Here myweb is your image tag

B. Now We Create 3 Jobs as Mentioned Earlier On Jenkins

You can go ahead and check the article [here](https://www.linkedin.com/pulse/integrating-github-branches-jenkins-docker-kevin-daniel-goveas)




