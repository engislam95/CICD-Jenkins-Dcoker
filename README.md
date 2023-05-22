# CICD-Jenkins-Dcoker

How to make cicd using jenkins and running docker in a jenkins container

- If you wondering how to dockarize your app first you can follow steps from this repo :
- https://github.com/engislam95/React-Docker

---

First of all let's understand some concept about Jenkins :

- Jenkins ?

* Jenkins is a popular continuous integration and delivery (CI/CD) tool. Jenkins is open source and has a great developer community that maintains its existing software and builds plugins to increase its functionality.

---

- To follow along with this article, you must have:

* Working knowledge of Docker and the terminal.
* You would like to make cicd using jenkins and listen to your dockarized project.

---

- Setting up Jenkins in Docker to run Docker

* To set up Jenkins in Docker to be able to run Docker (specifically: build, run, and push an image).
* Create a custom Jenkins Docker image and bind-mount the container to the host system daemon.

---

- Creating a custom Jenkins image

* First let's create Dockerfile and add the following command listed in the repo that contain the following info :

  - The FROM command tells Docker the base image (jenkins/jenkins:lts) from which to build the custom image.
  - The first RUN command updates all essential packages using apt-get update. Then installs the new ones needed for the custom Jenkins image using apt-get install.
  - The following RUN command downloads the Docker Linux Debian distribution CLI. Then the next one adds it to the repository.
  - And the last RUN command adds Jenkins user to the Docker group.

* To build the custom Jenkins image, run:

  - docker image build -t custom-jenkins-docker .

* Store Jenkins data :

  - docker run -it -p 8080:8080 -p 50000:50000 -v /var/run/docker.sock:/var/run/docker.sock -v jenkins_home:/var/jenkins_home custom-jenkins-docker

    - Expose port 8080 => by default run on that port (jenkins will be running on this port ).
    - Expose port 50000 => master / slave communication.
    - Run in detached mode (-d) => run container in background.
    - Bind named volume => presist data of jenkins.

* Finally :

* Open port 8080 in your browser and enter the password appears when running the previous command.
* Start installing recommended plugins.
* Create your first item and try to log the docker and docker-compose versions.

* References :

- https://hackmamba.io/blog/2022/04/running-docker-in-a-jenkins-container/

-- You can find many commands on the official documentation : https://docs.docker.com/engine/reference/commandline/docker/ .

Thanks
Islam Baidaq
