[docker](https://docs.docker.com/get-started/docker-overview/)

Docker is a platform that allows you easily scale your application through docker containers and docker images. 

## Containers
[docker containers](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-a-container/)

Docker containers are isolated processes for each app component. So if you have a frontend, backend and database, you can isolate each component in their own docker container to run.

Each container is independent to each other

## Images
[docker images](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/)

A docker image is an environment to configure and set up files for containers so you can effectively run them. 

So for instance if you have a python app, the docker image will have the python package, your code and the dependencies to run your code.

Note a docker image is immutable so once an image starts running, no modifications can be made it.

Container images are composed of layers which each layer represent a set of filesystem changes to get the app running like, additions, deletions, or modifications.

If we go back to our python app example, when creating an image, the image is generated based on this specific layer pipeline starting from Debian Base:
1. The first layer (Debian) adds the basic commands and a package manager
2. The second layer installs python runtime and pip for dependency management
3. Third layer copies in an application's specific requirements.txt file
4. fourth layer grabs all of your app's dependencies 
5. fifth layer copies all of the actual source code of the application into the image

![[container_image_layers.webp]]

This is very scalable if you have multiple apps that use the same layering allowing you to save time:
![[container_image_layer_reuse.webp]]

We can create our own base image in the terminal:

```bash
docker run --name=base-container -ti ubuntu
#you'll now be in root@d8c5ca119fcd:/#

apt update && apt install -y nodejs


node -e 'console.log("Hello world!")'
# should print out "Hello world"

#commit our changes to docker as a new image layer (in a separate terminal)
docker container commit -m "Add node" base-container node-base

#we can view the layers of the image
docker image history node-base

#which should output the following:
#IMAGE             CREATED          CREATED BY       SIZE      COMMENT
#693e8ccd2ccf   17 seconds ago   /bin/bash           178MB     Add node

# in a separate terminal, we can prove that the image has nodejs permanently
docker run node-base node -e "console.log('Hello again')"

# We can finally remove the initial container created as we have our image 
docker rm -f base-container

```

We can now extend the image to build additional images by using our newly created image as a base:

```bash
# creating a new container within our newly created image
docker run --name=app-container -ti node-base

echo 'console.log("Hello from an app")' > app.js

# running our application we just made above
node app.js
# it should print "Hello from an app"

#now we commit those changes and save them as a new image
docker container commit -c "CMD node app.js" -m "Add app" app-container js-app

#which we can visualize our new docker image layer
docker image history js-app

#which should output the following
#IMAGE          CREATED          CREATED BY       SIZE      COMMENT
#cb67a99e39b3   28 seconds ago   /bin/bash        8.19kB    Add app
#693e8ccd2ccf   17 minutes ago   /bin/bash        178MB     Add node

# still in another terminal, we can boot up a new container using our image 
docker run js-app

# we can now remove the containers cause we done
docker rm -f app-container

```

### Building images 
[build images](https://docs.docker.com/get-started/docker-concepts/building-images/build-tag-and-publish-an-image/)

once your [docker file](Docker%20file) is complete you can run the following command to build it as an image:

```docker
docker build .
```

which once done should produce an image you can run:
```docker
docker run sha256:9924dfd9350407b3df01d1a0e1033b1e543523ce7d5d5e2c83a724480ebe8f00
```

but the image name is ugly but no matter this can be fixed with 