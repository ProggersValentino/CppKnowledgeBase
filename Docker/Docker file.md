[dockerfile](https://docs.docker.com/get-started/docker-concepts/building-images/writing-a-dockerfile/)

A docker file is text based document used to create container images where you can create a specific in one file instead of needing to use the terminal to manually configure an image:

```dockerfile
FROM python:3.13
WORKDIR /usr/local/app

# Install the application dependencies
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copy in the source code
COPY src ./src
EXPOSE 8080

# Setup an app user so the container doesn't run as the root user
RUN useradd app
USER app

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8080"]
```

The example above creates a python image container for a python app

## Docker file Instructions


```dockerfile

# specified what base image you want to build off from
FROM <image>

#creates and defines a target "working directory" where all files for the image will be copied to
WORKDIR <path>

# Copy files from main project directory and place them within the working directory create
COPY <project-source-path> <image-path>

# Run a specified command like: git commit -m "mesg"
RUN <command>

# Sets environment variable that a running container will use
ENV <name> <value>

#Configures the image to a particular port you want to expose the image to
EXPOSE <port-number>

# creates and sets a default user for all subsequent instructions
USER <user-or-uid>

# the default command a container will use when initializing in the image
CMD ["<command>", "<arg1>"]

```

