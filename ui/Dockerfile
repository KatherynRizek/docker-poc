# base image 
FROM node:13.7.0-alpine

# working directory
WORKDIR /app

ENV PATH /app/node_modules/.bin:$PATH

# install and cache app dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm install
RUN npm install react-scripts@4.0.3 -g

# add app
COPY . .

CMD ["npm", "start"]