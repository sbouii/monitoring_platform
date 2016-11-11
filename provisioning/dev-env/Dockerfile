FROM node:6.1-onbuild

RUN apt-get update && apt-get install -y build-essential
# Install ruby
RUN apt-get install -y ruby
# Install sass
RUN gem install sass
# install bower and gulp
RUN npm install -g bower gulp
# installing dependencies with bower
RUN bower install --config.interactive=false --allow-root

ENV NODE_ENV development
# Port 3000 for server
# port 35729 for livereload
EXPOSE 3000 35729


