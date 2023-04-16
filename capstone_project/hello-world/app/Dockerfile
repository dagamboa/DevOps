FROM node:16.13.1-alpine
COPY ./ /app
WORKDIR /app
RUN npm install
RUN npm run test
CMD npm start