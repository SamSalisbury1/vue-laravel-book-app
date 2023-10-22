# Use the official lightweight Node image
FROM node:14-slim

# Set the working directory
WORKDIR /app

# Copy both package.json AND package-lock.json
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy project files into the docker image
COPY . .

# Expose the port the app runs on
EXPOSE 3302

# Command to run your app using CMD
CMD ["npm", "run", "serve"]
