# hadoop-on-docker
Docker containers for building Hadoop Clusters

This repository hosts the code for building docker containers for Hadoop services. Using the code in this repository, we can build docker images for any Hadoop version and we can build Hadoop Clusters using those docker images.

This repository also has the code for running single node hadoop setup. With some additional configurations, we can setup multi-node Hadoop clusters, but that is covered in the other project hadoop-on-k8s.

# Steps to build the Hadoop docker image

1. Checkout the code.
2. Update the Hadoop version number in the Docker file. Currently the version number is 3.1.2
3. Execute the following docker build command to build the docker image for Hadoop.

`docker build . -t the-docker-image-name:version`

Eg:

`docker build . -t eiswar/hadoop:3.1.2`

# Steps to setup the single-node hadoop cluster

1. After building the image, update the image name in the docker compose file.
2. Create a directory in the docker host to store HDFS namenode and datanode data.
3. Update the volume mounts in the docker-compose file.
4. Start the Hadoop services using docker-compose using the following command

`docker-compose up`

Once the docker-compose is finished, the single-node hadoop cluster on docker will be up and running. It can be accessed using the IP address specified in the docker-compose file.

We can update the /etc/hosts file with the IP address and hostname for the hadoop node, we can access the resouce manager UI and file manager UI from the browser.

# Features

1. Automatic resource allocation for the mapreduce applications.
2. Automatic setup of the fair scheduler
3. This can be easily integrated with Kubernetes. Options for establishing SSH trusts between Hadoop master and worker pods in Kubernetes environment are added.

# To do

1. Enabling HDFS federation
2. Enabling Namenode High Availability

