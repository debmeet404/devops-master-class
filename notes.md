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
- docker container ls (-a flag for stopped container as well)
- docker container stop "container-id"

---

When we Install docker, we install 2 things
- docker client
- docker daemon
docker client sends the commands over to docker daemon to acutally execute them
Docker Daemon is responsible for local images, conatiners and pushing/pulling from the docker image registry

---

Reasons for popularity of Docker
- Light Weight (in comparison to VMs as they have similar use cases) [VMs : Hardware > Host OS > Hypervisor > Guest OS1 + Sofware1 + Application1 / Guest OS2 + Software2 + Application2 etc] Whereas [Docker : Hardware > Host OS > Docker Engine > Container1 / Container2]
- Standard App Packaging
- Multi Platform Support
- Isolated containers [Different VMs sharing the same host will affect each other. Whereas Containers are isolated.] [Problem with one container wont spread to other containers]


---

More Commands : 
- docker pull mysql --> Only for pulling an image from registry, it does not launch the container [docker run would pull if not available and start as well]
- docker search mysql --> all images that are available on registry will be shown
- docker image history mysql --> all details about the layers in that docker image [we can also use image-id instead of name in this command]
- docker image inspect "image-id" --> provides a lot of data about the image
- docker container inspect "container-id"
- docker image remove "image-id"
- docker container rm "contianer-id"
- docker run command is a short form of docker container run command
- docker container pause "container-id"
- docker container unpause "container-id"
- docker container start is for restarting existing stopped containers, while docker container run is for creating and starting new container instances from images.
---
docker stop:

    Permanently stops the container: Terminates all processes running inside the container.
    Releases resources: Frees up the memory, CPU, and network resources used by the container.
    Loss of state: Any temporary data or changes made within the container are lost unless explicitly persisted before stopping.
    Use case: When you no longer need the container running and can afford to lose its state.

docker pause:

    Temporarily suspends the container: All processes in the container are frozen in their current state.
    Preserves resources: Memory used by the container remains allocated, but CPU and network resources are released.
    Maintains state: The container's memory state and any temporary data are preserved for when it's resumed.
    Use case: When you need to quickly interrupt the container but want to resume it later without losing its state.

---

Stop:

    Graceful termination: This is the preferred method. When you issue docker stop, the container receives a "SIGTERM" signal, gracefully telling it to shut down its main processes and perform any necessary cleanup before exiting. This allows applications within the container to perform critical tasks like saving data or closing connections, ensuring clean and consistent state.
    Safety and stability: Graceful termination minimizes the risk of data corruption or application inconsistencies, leading to a more stable and predictable experience. It's especially crucial for containerized applications handling sensitive data or interacting with external resources.
    Timeout and forceful stop: The container gets a reasonable chance to shut down gracefully. However, if it takes too long (configurable timeout), docker stop will forcefully terminate the container using a "SIGKILL" signal, effectively crashing it. This may lead to data loss or unexpected behavior.

Kill:

    Forceful termination: With docker kill, the container receives a "SIGKILL" signal directly, abruptly terminating all processes without any cleanup opportunity. This is akin to pulling the plug on a running computer.
    Data loss and instability: Forceful termination can lead to data corruption, incomplete operations, and unpredictable behavior within the container. It's generally discouraged as it can compromise stability and cause potential issues within the application or surrounding ecosystem.
    Use cases: docker kill can be helpful in rare situations where a container is unresponsive or stuck in a bad state. It's best used with caution and understanding of the potential consequences.

Benefits of graceful termination:

    Data integrity: Ensures proper data saving and closing of resources, minimizing the risk of corruption or loss.
    Application consistency: Guarantees the application finishes its tasks cleanly, leading to a consistent and predictable state.
    Stability and scalability: Promotes stable and reliable container operations, essential for robust and scalable applications.
    Reduced troubleshooting: Graceful termination minimizes the occurrence of issues and unexpected behavior, simplifying troubleshooting efforts.

----

docker start:

    Purpose: Resumes an already existing stopped container.
    Effect: Starts the container and initializes its processes from the point where it was stopped.
    Use case: When you need to continue working with a previously stopped container and want to retain its state.
    Note: Requires the container to be in a "stopped" state, not paused or exited.

docker unpause:

    Purpose: Resumes a previously paused container.
    Effect: Re-integrates the container back into the system, enabling resource allocation and process execution.
    Use case: When you temporarily paused a running container and want to resume its operation without losing its current state.
    Note: Requires the container to be in a "paused" state.

docker run:

    Purpose: Creates and starts a new container from a specified image.
    Effect: Downloads the image if needed, prepares the container environment, and runs the defined command or entrypoint.
    Use case: When you need to launch a new instance of an application based on an image.
    Note: Creates a new container even if an existing one with the same name exists.

Here's a table summarizing the key differences:
| Feature | docker start | docker unpause | docker run |
|---|---|---|---|
| Existing container | Must exist and be stopped | Must exist and be paused | Doesn't need to exist |
| Image download/build | None | None | Downloads or builds if needed |
| Command execution | No command is run, user needs to use `docker exec` later | Starts the configured command or entrypoint | Runs the specified command or entrypoint |
| Resource allocation | Starts resource allocation | Re-integrates into resource allocation | Allocates new resources |
| State preservation | Resumes previous state | Resumes previous state | Starts a new state |
| Use case | Resume stopped container | Resume paused container | Launch new application instance |

---

- docker container prune : remove all stopped containers

- docker system COMMAND --> used to Manage Docker
    - Commands:
    - df:          Show docker disk usage
    - events:      Get real time events from the server
    - info:        Display system-wide information
    - prune:       Remove unused data
- docker stats "container-id"


---

- docker build -t debmeet404/python-test:1 . >>>>> Building docker image from Dockerfile.
- -t for tag of the image
- there is a "." at the end which is the build context
- push to docker hub : docker push debmeet404/python-test:1


---

CMD vs ENTRYPOINT:

    CMD: Use for default commands that might be changed at runtime or when supporting multiple entry points for an image.
    ENTRYPOINT: Use for containers with a specific, fixed executable that should always run, even when arguments are provided.

---

- docker network ls
- docker network inspect bridge 
- two docker containers in bridge network mode cannot communicate with each other
- docker network create currency-network --> create a custom network
- docker run -d -p 8000:8000 --network=currency-network --name=currency-exchange 1ec
--> launch container in custom network with a custom container name


---

- docker compose up [directory should have docker compose file]
- add -d flag for detached mode
- docker compose down
- docker compose events
- docker compose config --> helps validate the yaml file
- docker compose images
- docker compose ps
- docker compose top
- docker compose pause/unpause
- docker compose stop/kill


