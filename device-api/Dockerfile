FROM node:17-alpine

# Create app directory
WORKDIR /usr/src/app

COPY package.json /usr/src/app

RUN npm install

# Bundle app source
COPY . .

EXPOSE 8080
CMD [ "npm", "start" ]