FROM alpine

RUN apk update
RUN apk add vim
RUN apk add emacs

ENTRYPOINT vim

# The FROM command sets the base image for the rest of the instructions
# We use the apk command to manage packages.
# The update fetches the current package index before adding the package
# The ENTRYPOINT specifies a command that will always be executed when the container starts
# To launch: docker build -t ex00:alpine .
# To check: docker run -it alpine
# To launch vim: vi
# docker rm -f $(docker ps -a -q)
