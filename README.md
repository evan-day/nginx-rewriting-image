# Nginx URL Rewrite Image

**Project Overview**

Having the HTML extension at the end of a file name is sort of ugly. Webservers can handle rewrites so that a request for a file will remove that file extension but preserve the content. The idea here, is to write a Docker image using Nginx as the base layer so that this can happen inside a container. With this, we could then use the new image as the base for any static websites that we want to run

### Status - Initial Stages

New project that we're just planning out right now

### Technical Details

* End goal is to have a Docker image that can be referenced in container based deployments of websites.
* Will most likely be able to find something on Stackoverflow that accomplishes our goals
* Passing in an Nginx configuration file as part of a Docker build from the base nginx image, will most likely be all that we need to do
