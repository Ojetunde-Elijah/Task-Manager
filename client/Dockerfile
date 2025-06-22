# Use official Node image
FROM node:20-alpine

# Set working directory
WORKDIR /app

# Copy package.json files first
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy all files
COPY . .

# Build the React app (Vite)
RUN npm run build

# Serve using preview mode (or use nginx if preferred)
EXPOSE 5173
CMD ["npm", "run", "preview"]
