
FROM node:latest as build-stage

COPY . /src

# Go to the directory in which the .go file is
WORKDIR /src
RUN echo "VUE_APP_API_ENDPOINT=\"http://127.0.0.1:4001/api\"" > .env.production
# Install the dependencies of the project
RUN npm install

# Build the app
RUN npm run build

FROM nginx as production-stage
RUN mkdir /app

COPY --from=0 /src/ .
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80


