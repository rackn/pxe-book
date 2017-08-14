



Cloud Init
==========

Cloud-init, short for cloud initialization, is a cloud-based pattern for injecting configuration information into a newly provisioned system.  

Each server is assigned an initialization file with the details it needs to come online.  Cloud-init can substitute for a Preseed/Kickstart configuration, but the server still requires something to execute the cloud-init file.  Cloud-init does not eliminate configuration, but rather changes the tools used for configuration.  

There is a technology called curtin, which is an Ubuntu technology, that will read a file and do post-configuration, similar to Preseed/Kickstart.  However, curtin creates another challenge by requiring a unique file for each server in order to inject server-specific information.  

In cloud, this pattern is much simpler because the servers are pretty much same there.  To do it in hardware requires more information about the servers to build cloud-init files so they can then drive the correct configuration.  

Cloud-init is very popular in immutable operating systems such as container Linux (previously coreOS), or Linuxkit or atomic where Preseed/Kickstart-type configurations are not supported due to the immutable OS.  

The idea behind immutable OS is that the install image does not get configured.  Instead, a pre-packaged image that should not be changed is sent down.  Once the image is installed, the system runs a script to get the information needed to configure itself.  So in practice the configuration is still there, but it has the advantage of being a much more repeatable way to do an install because installation for every server will be identical, plus the one pre-packaged image file.  

The value of cloud-init is in being highly intuitive to people with cloud experience.  Furthermore, cloud-init could be used for highly versatile development if it is possible to integrate cloud-init and physical machines.  The goal is to be able to take files in cloud that are used for cloud-init, add extra hardware, and have it work for physical machines.  

<insert story from rob about why it's useful to have cloud and metal shared ownership>


