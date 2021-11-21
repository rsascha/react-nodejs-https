
# my-workspace

Subject: Provide a React / NodeJS application via HTTPS

This is a Nx workspace (monorepo tool) provided by https://nx.dev/ containing a React FE and NodeJS Express BE.

To get the sample application running, follow the instructions below. 

To get your custom React / NodeJS application running, read the instructions and adjust the file system path settings. Maybe it's a good idea to get this sample running, before you switch to your custom configuration.

The path to the git repository on my machine: `/home/sascha/development/react-nodejs-https`

## Nx Setup

You need to have something like: 

```plain
node version: 16.13.0
npm version:  8.1.0
```

You need to install `nx`:

```sh
npm install nx --global
```

## Build Sample Project

Build the API and the React application:

* `nx run api:build` will create `dist/apps/api`.
* `nx run my-application:build` will create `dist/apps/my-application`.

## Setup NGINX

What I did:

```sh
brew install nginx
```

Output:

```plain
Docroot is: /home/linuxbrew/.linuxbrew/var/www

The default port has been set in /home/linuxbrew/.linuxbrew/etc/nginx/nginx.conf to 8080 so that
nginx can run without sudo.

nginx will load all files in /home/linuxbrew/.linuxbrew/etc/nginx/servers/.

To restart nginx after an upgrade:
  brew services restart nginx
Or, if you don't want/need a background service you can just run:
  /home/linuxbrew/.linuxbrew/opt/nginx/bin/nginx -g daemon off;
```

Use `brew info nginx` to get information about your setup.

My `/home/linuxbrew/.linuxbrew/etc/nginx/nginx.conf` looks like: [nginx.conf](./resources/nginx.conf.md)


So - I don't need to modify the `nginx.conf`. 

Notice the line: 

```nginx
include servers/*;
``` 
nginx will load all files in `/home/linuxbrew/.linuxbrew/etc/nginx/servers/`.

Create a file `/home/linuxbrew/.linuxbrew/etc/nginx/servers/my-workspace.conf` with the content:

```nginx
include '~/development/react-nodejs-https/my-workspace/infrastructure/nginx'
```


