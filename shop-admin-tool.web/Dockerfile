FROM node:16-alpine as builder
WORKDIR '/app'
COPY package.json .
COPY package-lock.json .
COPY . .
RUN npm run build

FROM builder as test
RUN npm run test -- --watchAll=false

FROM test as runtime
CMD ["npm", "start"]