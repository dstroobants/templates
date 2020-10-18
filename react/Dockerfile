FROM node:latest

RUN npm install -g create-react-app
RUN create-react-app my-app

COPY /app /my-app
COPY package.json .

RUN cd my-app

CMD ["yarn", "start"]
