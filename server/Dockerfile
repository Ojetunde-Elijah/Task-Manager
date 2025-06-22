# Use official Node image
FROM node:20-alpine

# Set working directory
WORKDIR /app

# Copy package.json files first for caching
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy rest of the server code
COPY . .

# Expose port
EXPOSE 5000

# Run the app
CMD ["node", "server.js"]
