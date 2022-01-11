FROM node:14 AS build
WORKDIR /opt/app
ADD *.json ./
RUN npm install
ADD . ./
RUN npm run build api

FROM node:14
WORKDIR /opt/app
ADD package.json ./
RUN npm install --only=prod
COPY --from=build /opt/app/dist/apps/api ./dist
RUN npm run build api
CMD ["node", "./dist/apps/api/main.js"]