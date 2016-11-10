# Tells the Docker which base image to start.
FROM node:6.6.0

# Adds files from the host file system into the Docker container.
ADD . /app

# Sets the current working directory for subsequent instructions
WORKDIR /app

RUN npm install
RUN npm install -g bower
#RUN bower install --allow-root
RUN npm install -g nodemon

# Expose a port to allow external access
# for NodeBB
EXPOSE 4567

# Start mean application
### CMD ["nodemon", "server.js"]

ENV NODE_ENV=production \
    daemon=false \
    silent=false

CMD ["npm", "start"]`