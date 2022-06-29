AMP allows you to deploy individual instances inside containers in order to isolate them from the host.

Note that `ampinstmgr` and ADS based instances cannot be run inside containers, as they need the ability to create them.

 * Install [Docker](https://docs.docker.com/install/) for your platform.
 * Add the AMP user to do the docker group by running `usermod -a -G docker amp`
 * In ADS, go to Configuration -> New Instance Defaults -> Create in Docker Containers
 * Restart the AMP service by running `systemctl restart ampinstmgr`

Now instances created via ADS will be created inside containers automatically. No additional configuration is required.

You can also use the `--docker` flag when creating instances via ampinstmgr. E.g. `ampinstmgr --docker create rust`