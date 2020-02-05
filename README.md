# Nginx URL Rewrite Image

Rewrite URLs for static content to make them look a whole lot prettier.

## How This Works

Based on this answer from [StackOverflow](https://stackoverflow.com/questions/38228393/nginx-remove-html-extension), we use the configuration listed in the initial question and the location block used in the accepted answer. Using the Nginx image as a base, we pass in this configuration file to be the default configuration. We then build the Docker image and publish it to Github Packages. Since we use the same, default location for storing static content, we can just replace the use of Nginx in any image with this image.

As a result, if we have a HTML file called `about-me.html`, we can just visit the URL `/about-me` and we will get the HTML file returned. On the flip side, visiting a URL with the `.html` extension in it, will remove the extension. The answer on Stackoverflow is more in depth in its explanation and how the configuration file works. This just simply takes that configuration which you may use in a vanilla Nginx installation and runs it in Docker :)

### Known Issues

* In Kubernetes, attempting to access a HTML file directly appears to eventually cause a time out. Workaround will be to any links that are used in the websites will directly refer to the pretty URL and not the file itself.
