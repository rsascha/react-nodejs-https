
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

More information: [infrastructure/nginx/README.md](infrastructure/nginx/README.md)

## Start Everything

```sh
npm install
npm run api
npm run nginx
```

If this is not working, check out: [infrastructure/nginx/README.md](infrastructure/nginx/README.md)