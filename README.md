middleman-nginx
===============

A base container to serve Middleman content using Nginx. Saves memory and deploy time.

You don't need to use Middleman to serve your site - you can just compile the files and use anything - `middleman build`

This is a container that has Ruby and Middleman available, to compile and build the static site, that nginx serves.

You can use our container: `docker pull octohost/middleman-nginx`

Or you can build your own:

```
docker build -t your-name-here/middleman-nginx .
docker push your-name-here/middleman-nginx
```

After this - just add this Dockerfile to your Harp repo:

```
FROM octohost/middleman-nginx

WORKDIR /srv/www

ADD . /srv/www/
RUN middleman build

EXPOSE 80

CMD nginx
```

Push it to your docker server - and your server will use 4-6MB of RAM instead of 60MB.

To see an example working repo, [take a look here](https://github.com/octohost/middleman).
