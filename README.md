# Devops Engineer Test

This is a simple (and hopefully fun) exercise, used to evaluate your ability to set
up a basic server environment, running a number of applications across a set
of technologies. Your solution must come in the form of a **Vagrant** VM (see below for requirements) -
you should provide your `Vagrantfile` and a brief explanation of your approach.
You can just clone this repository and build on top of it, but please do not fork it,
as that will make your solution visible to others.

This repo includes three web services under `/application`:

 * **Cat**: A NodeJS application, binding to port `3000` when run, serving the
            image of a cat under the `/show` URL. It requires NodeJS `8.x` to run,
            but otherwise already includes all application dependencies under `node_modules`.
 * **Goat**: A Java application, binding to port `9000` when run, serving the
             image of a goat under the `/show` URL. It requires Java 8 to run,
             but otherwise all application dependencies are packaged into the
             provided JAR file.
 * **Dog**: A PHP application, serving the image of a dog under the `/show` URL.
            It has no external dependencies, but it does require a **PHP-FPM + Nginx**
            environment to run. While it works under any recent version of PHP, you should use PHP 7.


## The Task

You must:

  * Starting with your preferred distro, set up a Vagrant box for running Docker containers
  * Create a Docker image for each of the above web services. These are just for running the services
    on the VM, and do not need to be published to a registry.
  * Exposed on port 80 of the VM, set up an Nginx container with the following behaviour:
    * All requests to `/dog` are proxied to `/show` on the **Dog** service
    * All requests to `/cat` are proxied to `/show` on the **Cat** service
    * All requests to `/goat` are proxied to `/show` on the **Goat** service
    * All other requests and any errors should result in the custom error
      page (`application/error.html` in this repo) being served
  * Include basic documentation on your approach and implementation in a README file

You don't have to worry about logging, monitoring or scalability at this time - the key here is simplicity. That being said, you're welcome to elaborate in your README on the tools you would use to cover these key areas, and any other improvements you would make if given more time or freedom in implementation.

You're free to use any distro and provisioning tools when setting up your server,
but ultimately all of the above must work after a single execution of `vagrant up`.

Finally, take care not to over-engineer your solution!
