# A Developer's Introduction to Containers

Nigel Brown, VMWare

  * A container is a process or group of processes running in isolation.
  * Uses features of linux kernel
    * Namespaces
    * cgroups - control groups
  * Process Isolation
  * Operating System Virtualization
  * chroot
    * changes the root directory
    * app only see files under specified directory as /
  * lxc - 2008
  * docker - 2013
    * lib container - open source
    * donated to open container initiative
  * open container specification
    * containerd - a full reference implementation of the runtime
  * github.com/pa-brown/containers-info
  * Docker file
    * build image
    * store in repository
    * create container
  * Docker containers are built in layers. Each line in the docker file relates to a layer. Layers are hashed & cached to spend up builds. 
    * For performance put lines that will change most frequently at the bottom. Docker rebuilds from the line that changed down.
    * Entrypoint is encoded into the image
    * CMD can be overriden when creating the container as a command line option
  * docker build -t something/container:version
  * docker run -p 4567:80 something/container:version
  * Deploying image to a repository is a push
    * docker push containername
    * 