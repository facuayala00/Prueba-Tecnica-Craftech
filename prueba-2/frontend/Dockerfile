# Use Node.js 16 as base image
FROM node:16

# Set working directory 
WORKDIR /app

# Add /app/node_modules/.bin to $PATH 
ENV PATH /app/node_modules/.bin:$PATH

# Install app dependencies
COPY package.json .
RUN npm install

# Add app
COPY . .

# Start the app
CMD ["npm", "start"]