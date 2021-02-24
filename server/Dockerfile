FROM golang:1.14
EXPOSE 4000

# Node and npm installation

ENV NODE_VERSION=14.15.5
RUN apt install -y curl
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
ENV NVM_DIR=/root/.nvm
RUN . "$NVM_DIR/nvm.sh" && nvm install ${NODE_VERSION}
RUN . "$NVM_DIR/nvm.sh" && nvm use v${NODE_VERSION}
RUN . "$NVM_DIR/nvm.sh" && nvm alias default v${NODE_VERSION}
ENV PATH="/root/.nvm/versions/node/v${NODE_VERSION}/bin/:${PATH}"
RUN node --version
RUN npm --version

# I was getting a Permission denied error and apparently this fixes it
RUN npm config set user 0
RUN npm config set unsafe-perm true
# Installing vue
RUN npm install -g @vue/cli -y 
RUN npm install @vue/cli-service -g

# Installing git 
RUN apt-get -y install git

# Clone the repository
RUN pwd && ls
COPY . /server
RUN pwd && ls
# RUN git clone https://github.com/jdmendozaa/vuego-demoapp.git

# Go to the directory in which the .go file is
WORKDIR ./server
# Build the app
RUN echo "halp" && ls
RUN go build 
RUN echo "Build the go app"
RUN ls
CMD ["./vuego-demoapp"]

# Running the file 
# COPY bootstrap.sh /go/src

# RUN ["chmod", "+x", "bootstrap.sh"]
# ENTRYPOINT ["./bootstrap.sh"]
