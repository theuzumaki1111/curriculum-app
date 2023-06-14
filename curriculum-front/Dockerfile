FROM node:lts-alpine
WORKDIR /usr/src/app
COPY curriculum-front/package*.json ./
RUN ls -l
RUN npm install
COPY curriculum-front ./
RUN ls -l
RUN npm run build
COPY nodeServer.js dist/nodeServer.js
WORKDIR /usr/src/app/dist
EXPOSE 8181
CMD [ "node", "nodeServer.js" ]
