# Use a lightweight Node.js environment
FROM node:18-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy package files first to leverage Docker cache
COPY package*.json ./

# Install only production dependencies
RUN npm install --production

# Copy the rest of your server code
COPY . .

# Your backend runs on port 5000
EXPOSE 5000

# Command to start your server
CMD ["node", "server.js"]