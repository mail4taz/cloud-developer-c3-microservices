#Base image for the container
FROM node:current AS builder

WORKDIR /home/node/app
    
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied where available (npm@5+)
COPY package*.json ./
RUN npm ci

COPY . .
EXPOSE 8082
CMD [ "npm", "run", "prod" ]
