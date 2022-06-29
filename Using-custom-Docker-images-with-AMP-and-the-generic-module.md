New to AMP 2.2.2.0 is the ability to easily use customised Docker images when creating and running instances inside docker.

Prior to this, running your own images was achieved by having the Generic module run `docker` directly which is less elegant and doesn't integrate as tightly.

This method makes it easier to leverage the 'common' AMP base while adding your own requirements, such as extra tools/libraries (nodejs, npm, mongodb) without it cluttering up the host and without having to lose AMPs manageability and control.

# Sample dockerfile

Your dockerfile must be FROM the ampbase image. Existing images cannot be used unmodified.

The following dockerfile expands upon the standard base image to add NodeJS, which would allow you to run applications that depend on it.

```
FROM cubecoders/ampbase

RUN apt-get update && apt-get -y upgrade && \
        apt-get install -y nodejs npm && \
        apt-get clean && \
        rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/ampstart.sh"]
CMD []
```

The `ampbase` image dumps the apt cache, so it's necessary to run an `apt-get update` first to get the repo list. The upgrade is optional and simply means you can use a newer base package than the official base image.

After that you can install whatever other packages and dependencies you like. This script also then cleans the apt cache again to save on space.

The `ENTRYPOINT` and `CMD` lines need to remain as-is to start the AMP instance that will be running inside the container. AMP itself will then take responsibility for actually running the application. `ampstart.sh` comes from the base image and is responsible for taking care of dropping permissions and then invoking AMP with the appropriate arguments.

# Accessing data

The AMP instance itself gets mounted at `/AMP/` inside the container. AMP uses mount binds so the base instance data exists within AMPs normal directory structure on the host.

So for example, if you had an instance called `NodeJSApp01` - it would likely be located at `/home/amp/.ampdata/instances/NodeJSApp01` on disk on the host, but within the container it will always be at `/AMP/` regardless.

# Using your custom image

For configurations based on the Generic module, simply add the following to your applications KVP file:

```
Meta.SpecificDockerImage=MyName/MyImage
```

Instances created based on this configuration from ADS will automatically use your specified image when created. If you use an image from the public registry it will automatically be downloaded.

This information is also reflected in `instances.json` - where each instance has the `SpecificDockerImage` field in its metadata. You can alter this directly if necessary (such as during development or to change an existing instances base image).