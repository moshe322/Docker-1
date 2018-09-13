FROM ruby

RUN apt-get update -y && apt-get upgrade -y
RUN gem install rails
RUN apt-get install nodejs -y

ONBUILD COPY . /opt/app

ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle install
ONBUILD RUN rails db:migrate
ONBUILD RUN rails db:seed

# docker build -t test01ex02 .
# docker run -v /var/www:/var/www -p 5000:80 -t test01ex02

# The ONBUILD instruction adds to the image a trigger instruction to be executed at a later time, when the image is used as the base for another build.
# This is useful if you are building an image which will be used as a base to build other images
# At the end of the build, a list of all triggers is stored in the image manifest, under the key OnBuild. They can be inspected with the docker inspect command.
# Later the image may be used as a base for a new build, using the FROM instruction. As part of processing the FROM instruction, the downstream builder looks for ONBUILD triggers, and executes them in the same order they were registered. If any of the triggers fail, the FROM instruction is aborted which in turn causes the build to fail. If all triggers succeed, the FROM instruction completes and the build continues as usual.
# https://docs.docker.com/engine/reference/builder/#onbuild
# Start by setting up the four files needed to build the app. 
# https://docs.docker.com/compose/rails/
# In order to control our database schema and to make deployment and changes easier we can use migration files. A migration file is a set of instructions that will be run against your database.
# Seed creates the database
