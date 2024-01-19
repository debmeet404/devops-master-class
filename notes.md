DevOps is a set of practices that aim to improve collaboration and communication between software development (Dev) and information technology operations (Ops) teams. The goal is to automate the process of software delivery and infrastructure changes, ensuring a faster and more reliable delivery of software products. The term "DevOps" is a combination of "development" and "operations."

Key principles and practices of DevOps include:

    Collaboration: Encourages close collaboration and communication between development, operations, and other stakeholders involved in the software development lifecycle.

    Automation: Utilizes automation tools for building, testing, deployment, and infrastructure provisioning. Automation helps reduce manual errors, increases efficiency, and speeds up the delivery process.

    Continuous Integration (CI): Developers integrate their code changes into a shared repository frequently, and automated builds and tests are triggered upon each integration. This ensures early detection of issues.

    Continuous Delivery (CD): Extends CI by automatically deploying code changes to testing, staging, and production environments. CD ensures that software is always in a deployable state.

    Infrastructure as Code (IaC): Infrastructure configuration and management are treated as code, allowing for the automated provisioning and management of infrastructure resources.

    Monitoring and Logging: Continuous monitoring of applications and infrastructure, coupled with logging and analysis, helps identify and address issues quickly, improving overall system reliability.

    Version Control: Utilizes version control systems (e.g., Git) to manage and track changes to source code, configuration files, and other artifacts.

    Microservices and Containers: Encourages the use of microservices architecture and containerization technologies (e.g., Docker) to create scalable and flexible systems.

    Feedback Loops: Encourages the use of feedback loops for continuous improvement. This includes gathering feedback from users, monitoring system performance, and evaluating the effectiveness of development and operations processes.

---

DevOps practices aim to break down silos between development and operations teams, fostering a culture of collaboration and shared responsibility. By implementing DevOps, organizations can achieve faster and more reliable software delivery, improve efficiency, and enhance overall system stability.

---

First we started with Waterfall model 

3 Important points found for better software development : 
- better communication
- look for scope of automation
- get early feedback

---

Next was Agile model
- Software was built in small iterations called Sprints
- All the steps of the Waterfall model were followed but, now not over a long period, but over smaller sprints
- Agile improved the communication by introducing the concept of a product owner/product manager, who is who is always available for the software team to work with
- Agile improved on the automation part by writing UTs, Integraiton Tests, Automated Code Quality checks etc Eg - Jenkins
- Agile improved the feedback process as well, at the end of the sprint the state of the project can be demoed to the involved stakeholders
- Agile also improved the feedback by the continuous integraiton CI. If some new feature is added, and a UT fails, that actually provides quick feedback to the dev

---

Microservices Became Popular
- With increase in microservices, the number of deployment units increased. This lead to operations part becoming more important.
- With the above problem, devops also became popular

---

DevOps
- Better communication between development and operations teams. Also in standups of devs, operations pocs were added. Teams understood each others processes and problems
- Make software deployment easier
- Devops teams were in charge of automation as well, They try to automate the following : 
    - Create Template
    - Provision Server
    - Install Software
    - Configure Software
    - Deploy the App

---

The Key Terminologies of DevOps : 
- Continuous Deployment [CI + addition of deployment step]
- Continuous Delivery [CD + UAT deployment(user acceptance testing) + prod release]
- Infrastructure as Code IAC [Treating infra as code]

---

Containerization : 
- An org may be having multiple microservices and all microservices written different tech stacks and have different deployment procedures and different deployment environment setups
- Containerization provides us the option to create a docker image out of our code. Now once we have the image with our microservice code, the images of various different microservices can be deployed in the exact same fashion.
- Docker simplifies the deployment step and also helps avoid any manual errors.
- sudo docker run -p 5000:5000 in28min/hello-world-python:0.0.1.RELEASE
- hub.docker.com : docker registry
- running version of an image is called a contianer
- sudo docker run -d -p 5002:5000 in28min/hello-world-nodejs:0.0.1.RELEASE [-d for detached mode] [it outputs the container id that is started]
- docker logs "container-id"
- docker logs -f "container-id" [logs are attached to the terminal]
- docker images
- docker container ls
- docker container stop "container-id"

