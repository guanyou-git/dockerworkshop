FROM node:latest

# Set environment variables
ENV APP_ROOT=/app APP_PORT=3000

# Create directory and cd into it
WORKDIR ${APP_ROOT}

# Add files into the WORKDIR, directory have to specify name
ADD main.js .
ADD package.json .
ADD public public
ADD views views

# Run some command
RUN npm install

# Expose the port our container will be exposing
EXPOSE ${APP_PORT}

# Add healthcheck to the application
HEALTHCHECK --interval=10s --timeout=5s --retries=3 \
    CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1


# Command that will start up the container
ENTRYPOINT [ "node", "main.js" ]

# Run is during buildtime
# During execution, can use cmd / entrypoint.
# Entrypoint is fixed, this is how application is runned, CMD would be runn'ed after entrypoint and it will be overwritten (more flexibilty)
CMD [ "" ]
