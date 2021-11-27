
# my-workspace

Subject: Provide a React / NodeJS application via HTTPS

This is a Nx workspace (monorepo tool) provided by https://nx.dev/ containing a React FE and NodeJS Express BE.

To get the sample application running, follow the instructions below. 

To get your custom React / NodeJS application running, read the instructions and adjust the file system path settings. Maybe it's a good idea to get this sample running, before you switch to your custom configuration.

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

## Setup bash auto complete

```sh
brew install bash-completion@2
```

Follow instructions: Add the following line to your ...

I had to use `.bashrc` instead of `.bash_profile` to get it running.

Test: 
* Open a new terminal
* `cd infrastructure/nginx`
* `make ` [TAB] [TAB] should show the Makefile targets: start, etc. 

## Setup NGINX

What I did:

```sh
brew install nginx
```

## Use NGINX

Follow: [infrastructure/nginx/README.md](infrastructure/nginx/README.md)
