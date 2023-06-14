FROM node:latest
WORKDIR /usr/src/app
COPY package*.json ./
RUN ls -l
RUN npm install
COPY . . 
RUN ls -l
RUN npm run build
COPY curriculum-front/nodeServer.js dist/nodeServer.js
WORKDIR /usr/src/app/dist
EXPOSE 8181
CMD [ "node", "nodeServer.js" ]
