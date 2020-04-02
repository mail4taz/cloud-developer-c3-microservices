#Base image for the container
FROM node:current AS builder

WORKDIR /home/node/app
    
# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied where available (npm@5+)
COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run tsc

FROM node:current-alpine  
RUN apk --no-cache add ca-certificates bash vim
WORKDIR /home/node/app
COPY --from=builder /home/node/app ./
EXPOSE 8082
CMD [ "node", "./www/server.js" ]
