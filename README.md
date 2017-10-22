# flpk-docker-image

## Start the container with

```
docker run -d -p 80:3838 -v /srv/shinyapps/:/srv/shiny-server/ -v /root/shiny.conf:/etc/shiny-server/shiny-server.conf fmichonneau/flpk-docker-image
```

with `/etc/shiny-server/shiny-server.conf` being:

```
# Instruct Shiny Server to run applications as the user "shiny"
run_as shiny;

# Define a server that listens on port 3838
server {
  listen 3838;

  # Define a location at the base URL
  location / {

    # Host the directory of Shiny Apps stored in this directory
    #site_dir /srv/shiny-server/;
    app_dir /srv/shiny-server/flpk-shiny;

    # Log all Shiny output to files in this directory
    log_dir /var/log/shiny-server;

    # When a user visits the base URL rather than a particular application,
    # an index of the applications available in this directory will be shown.
    directory_index on;
  }
}
```
