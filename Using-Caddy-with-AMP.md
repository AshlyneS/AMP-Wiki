### _This page was contributed by a member of the AMP community_

To use Caddy with AMP you can download the latest version from https://caddyserver.com/ or compile it yourself.

The configuration file below is experimental but should work, just change the domain at the top to yours.  Caddy automatically handles Let's Encrypt certificates and requires port 80 or 443 to complete the challenge.

The configuration file should be named `Caddyfile` and is put in the same directory as the executable.  Run `caddy fmt -overwrite` to format the Caddyfile. Caddy will then automatically load it.  You can start Caddy with the start command


Example Configuration
```
amp.yourdomain.com {
    @proxyamp {
        not path /shared/*
    }
    reverse_proxy @proxyamp localhost:8080

    route /shared/* {
        root * /opt/cubecoders/amp/shared/WebRoot/
        uri strip_prefix /shared
        file_server
    }
    
    handle_errors {
        @502 {
            expression {http.error.status_code} == 502
        }
        root * /opt/cubecoders/amp/shared/WebRoot
        rewrite @502 /NotRunning.html
        file_server
    }
}
```

For Windows recovery mode isn't supported

```
amp.yourdomain.com {
    reverse_proxy localhost:8080
}
```
