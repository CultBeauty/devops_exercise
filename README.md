# Devops Engineer Test

This is a simple (and hopefully fun) exercise, used to evaluate your ability to set
up a basic server environment, running a number of applications across a set
of technologies. Your solution must come in the form of a **Vagrant** VM (see below for
requirements). You can just build on top of this repository, but please don't fork it,
as this will make your solution publicly visible from this repo to everyone!

This repo includes three web services under `/application`:

 * **Cat**: A NodeJS application, binding to port `3000` when run, serving the
            image of a cat under the `/show` URL. It requires NodeJS version `0.10.x`
            or `4.2.x` to be installed, but otherwise already includes all application
            dependencies under `node_modules`.
 * **Goat**: A Java (Scala) application, binding to port `9000` when run, serving the
             image of a goat under the `/show` URL. It requires Java 8 to be installed,
             but otherwise all application dependencies are packaged into the
             provided JAR file.
 * **Dog**: A PHP application, serving the image of a dog under the `/show` URL.
            It will run under any version of PHP5 and has no external dependencies,
            but it is your job to set up an **Nginx + PHP-FPM** environment to make it work.


## The Task

You must:

  * Starting with your preferred distro, install all dependencies required by the
    above applications.
  * Using the init system available on your chosen distro, set up a service for
    running each of the applications (with the exception of the PHP app, which will
    run as part of PHP-FPM).
  * Bound to port 80, set up an Nginx Site with the following behaviour:
    * All requests to `/dog` are proxied to `/show` on the **Dog** service
    * All requests to `/cat` are proxied to `/show` on the **Cat** service
    * All requests to `/goat` are proxied to `/show` on the **Goat** service
    * All other requests and any errors should result in the custom error
      page (`application/error.html` in this repo) being served

You don't have to worry about anything else (logging, monitoring, etc.) at this time.
You're free to use any distro and provisioning tools when setting up your server,
but ultimately all of the above must work after a single execution of `vagrant up`.

Finally, take care not to over-engineer your solution!
