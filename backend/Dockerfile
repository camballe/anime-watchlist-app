# set the base image to create the image for react app
FROM node:20-alpine

RUN mkdir /app && chown node:node /app

# install pnpm globally
RUN apk add --no-cache git
RUN npm install -g pnpm

# # create a user with permissions to run the app
# RUN addgroup app && adduser -S -G app app

# # set the user to run the app
# USER root

# set the working directory to /app
WORKDIR /app

USER node
# install dependencies using pnpm before changing ownership
COPY package*.json ./
RUN pnpm install

# copy the rest of the files to the working directory
COPY . .

# # give the app user ownership of the /app directory and its subdirectories
# RUN chown -R app:app /app

# # change back to the app user
# USER app

# expose port 5173
EXPOSE 8000

# command to run the app
CMD pnpm start
