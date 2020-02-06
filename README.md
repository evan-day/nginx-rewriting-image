# Nginx URL Rewrite Image

Rewrite URLs for static content to make them look a whole lot prettier.

## How This Works

Based on this answer from [StackOverflow](https://stackoverflow.com/questions/38228393/nginx-remove-html-extension) (Thank you, [Arnon](https://stackoverflow.com/users/4175718/arnon)!), we use the configuration listed in the initial question and the location block used in the accepted answer. Using the Nginx image as a base, we pass in this configuration file to be the default configuration. We then build the Docker image and publish it to Github Packages. Since we use the same, default location for storing static content, we can just replace the use of Nginx in any image with this image. So an example, your Dockerfile can look like

```
FROM docker.pkg.github.com/evan-day/nginx-rewriting-image/nginx-rewrite-prod:latest
COPY ./ /usr/share/nginx/html
```

As a result, if we have a HTML file called `about-me.html`, we can just visit the URL `/about-me` and we will get the HTML file returned. On the flip side, visiting a URL with the `.html` extension in it, will remove the extension. The answer on Stackoverflow is more in depth in its explanation and how the configuration file works. This just simply takes that configuration which you may use in a vanilla Nginx installation and runs it in Docker :)

## Available Images

Two images are available for use

* `nginx-rewrite-prod` - Is the default image and is recommended to be used. This will only get rebuilt and redeployed on the merging of a pull request back into the master branch
* `nginx-rewrite-dev` - Is built when there's any branches that are not master being actively developed. It should probably not be used all too much!

## Known Issues

* In Kubernetes, attempting to access a HTML file directly appears to eventually cause a time out. Workaround will be to any links that are used in the websites will directly refer to the pretty URL and not the file itself.
