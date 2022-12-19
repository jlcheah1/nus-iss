FROM node:19

## 1 Building the application
WORKDIR /app

ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD views views		
ADD public public

# Install node modules
RUN npm ci

## Run the application
#Set the APP_PORT from main.js to 3000 as param
ENV PORT=5000 INSTANCE_NAME="Happy Bear" INSTANCE_HASH="Good Day"

## 2 Health check
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
	CMD curl -s http://localhost:${APP_PORT}/healthz || exit 1

#Expose port the application bind to
EXPOSE ${PORT}

# Start application
ENTRYPOINT node main.js