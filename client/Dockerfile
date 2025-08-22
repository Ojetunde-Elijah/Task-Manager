# ---- build stage: produce static files from React/Vite ----
FROM node:20-alpine AS build
WORKDIR /app

# Copy only manifests first (better layer cache)
COPY package*.json ./
RUN npm ci

# Copy the rest of the app (includes client/.env with only VITE_* vars)
COPY . .

# Build the React app; VITE_* envs are read at build time
RUN npm run build  # outputs to /app/dist

# ---- serve stage: nginx serves the static build on port 80 ----
FROM nginx:1.27-alpine
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
