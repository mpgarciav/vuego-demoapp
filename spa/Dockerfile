
FROM node:latest as build-stage
# COPY package*.json ./
RUN npm config set user 0
RUN npm config set unsafe-perm true
# lo del clone
# RUN git clone https://github.com/jdmendozaa/vuego-demoapp.git
COPY . /spa

RUN pwd && ls

# Go to the directory in which the .go file is
WORKDIR ./spa

# Install the dependencies of the project
RUN npm install

# Build the app
RUN npm run build
RUN echo "Vue app built"

# --- Running the app

RUN ls

FROM nginx as production-stage
RUN mkdir /app
RUN ls
# COPY --from=build-stage dist /app
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 4001

RUN ls