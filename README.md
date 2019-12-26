# Nginx URL Rewrite Image

Rewrite URLs for static content to make them look a whole lot prettier.

## Project Overview

Based on this answer from [StackOverflow](https://stackoverflow.com/questions/38228393/nginx-remove-html-extension), we use the configuration listed in the initial question and the location block used in the accepted answer. Using the Nginx image as a base, we pass in this configuration file to be the default configuration. We then build the Docker image and publish it to Github Packages. Since we use the same, default location for storing static content, we can just replace the use of Nginx in any image with this image.

### Status - Ready For Production

The development branch for this project was merged in to master and we can now find the production image within the packages for the repository.

### Technical Details

* End goal is to have a Docker image that can be referenced in container based deployments of websites.
* Will most likely be able to find something on Stackoverflow that accomplishes our goals
* Passing in an Nginx configuration file as part of a Docker build from the base nginx image, will most likely be all that we need to do

### Known Issues

* In Kubernetes, attempting to access a HTML file directly appears to eventually cause a time out. Workaround will be to any links that are used in the websites will directly refer to the pretty URL and not the file itself
