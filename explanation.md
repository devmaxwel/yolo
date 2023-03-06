1.  # Choice of the base image on which to build each container.
    When choosing a base image for a Docker container, it's important to consider factors such as security, stability, and compatibility with your application's dependencies. In my microservice assignment, I chose to use the node base image for my web and API services since my application is built using Node.js.
2.  # Dockerfile directives used in the creation and running of each container.

    ## Client Service Dockerfile

    FROM node:13.12.0
    WORKDIR /app
    COPY package\*.json ./
    RUN npm install
    COPY . .
    EXPOSE 3000
    CMD ["npm", "start"]

    1. FROM node:13.12.0 - Specifies the base image to use as the starting point for the Dockerfile. In this case, I'm using the node:13.12.0 image.
    2. WORKDIR /app - Sets the working directory for subsequent commands in the Dockerfile to /app.
       COPY package\*.json ./ - Copies the package.json and package-lock.json files from the local directory to the Docker image.
    3. RUN npm install - Runs the npm install command inside the Docker image to install the application's dependencies.
    4. COPY . . - Copies the entire local directory to the Docker image.
    5. EXPOSE 3000 - Informs Docker that the container will listen on port 3000.
    6. CMD ["npm", "start"] - Specifies the command to run when the container starts. In this case, it runs the npm start command to start the web server.

    ## Api Service Dockerfile

    1. FROM node:14-alpine
    2. WORKDIR /app
    3. COPY package\*.json ./
    4. RUN npm install
    5. COPY . .
    6. EXPOSE 3000
    7. CMD ["npm", "start"]

    The same directives are as explaine above.

3.  # Docker-compose Networking (Application port allocation and a bridge network implementation) where necessary.

    In my docker-compose.yml file, I specified a bridge network called yolo-network for my microservices to communicate with each other:
    I specified network driver to type bridge.

4.  # Certainly! I'd be happy to explain the Git workflow I used to achieve my microservice assignment with Docker.

    1. I forked the yolo repository from the provided link

    2. I cloned the repository to my local machine. I used the git clone command to clone the repository to my local machine.

    3. Create a Dockerfile for each microservice. I created a Dockerfile for each microservice in its respective branch. I followed best practices for writing Dockerfiles, such as using a lightweight base image and only including necessary dependencies.

    4. Build and test each Docker image locally. I used the docker build command to build each Docker image locally, and then used the docker run command to test each image to make sure it was running correctly.

    5. Create a docker-compose.yml file. I created a docker-compose.yml file in the main branch to orchestrate the containers for each microservice. I specified the Docker image for each service and defined the networking

    6. Test the Docker Compose setup locally. I used the docker-compose up command to start the Docker Compose setup locally and tested that the microservices were able to communicate with each other.

    7. Push the changes to the repository. Once I was satisfied that everything was working correctly, I committed and pushed the changes to the repository.

    8. Deploy the microservices to a production environment. I used a Docker-based hosting platform Heroku.

5.  # Successful running of the applications and if not, debugging measures applied.
    ## I deployed my docker compose file to heroku but at the moment my application is not running. I am still trying to debug my hosting service to see where the error is coming from like.
         1. checking the logs  with `heroku logs --tail`
         2. checking container logs `docker logs <container-name>`.
         3. Consult heroku documentation.
6.  # Good practices such as Docker image tag naming standards for ease of identification of images and containers.
    1. I used the repository name together with the service name to tag my images and versioning method to name my images
       `yoloclient:1.0.1`
       `yolobackend:1.0.1`
       2.I used lowercase letters to do this
