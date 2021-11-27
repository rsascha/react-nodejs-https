# Print help
print-help:
	nginx -h

# Start NGINX with minimal configuration in foreground to see error messages during startup and runtime. 
# Open: http://localhost:8080/
start-simple-test:
	nginx -c $(PWD)/config/simple-test/nginx.conf -e $(PWD)/logs/error.log -g 'daemon off;'

# Get the root of this workspace
export MY_WORKSPACE_ROOT = $(realpath $(PWD)/../..)

# Kill all NGINX processes
kill-all-nginx:
	killall nginx || echo OK

# Insert absolute path values to the NGINX configuration
generate-config:
	envsubst '$${MY_WORKSPACE_ROOT}' < $(PWD)/config/my-application/nginx.conf.template > $(PWD)/config/my-application/nginx.conf

# Start the application for debugging: https://localhost:8081
start-my-application-foreground: kill-all-nginx generate-config
	nginx -c $(PWD)/config/my-application/nginx.conf -e $(PWD)/logs/error.log -g 'daemon off;'

# Start the application in background: https://localhost:8081
start-my-application: kill-all-nginx generate-config
	nginx -c $(PWD)/config/my-application/nginx.conf -e $(PWD)/logs/error.log
	@echo "Now open: https://localhost:8081"

# Send a stop signal
stop-my-application:
	nginx -s stop

# Start your API, so that the reverse proxy can reach http://127.0.0.1:3333
start-api:
	npm run serve:api

# Build all your projects
build-all:
	npm run build:all
	
