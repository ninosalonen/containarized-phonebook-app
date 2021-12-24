FROM node:16 AS build-stage

WORKDIR /usr/src/app

COPY . .

RUN npm ci

RUN npm run build

FROM node:16

WORKDIR /usr/src/app

COPY --from=build-stage /usr/src/app/build /usr/src/app/build

RUN npm install -g serve

CMD ["serve", "build"]