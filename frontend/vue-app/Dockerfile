# Stage 1: Build Vue app
FROM node:20 AS build
WORKDIR /usr/src/app

COPY package*.json ./
COPY nx.json ./
COPY tsconfig.base.json ./
COPY eslint.config.mjs ./ 

# Install dependencies
RUN npm install --legacy-peer-deps

COPY . .

# Build the Vue app using Nx
RUN npx nx build vue-app --prod

# Stage 2: Serve with Nginx
FROM nginx:alpine
COPY --from=build /usr/src/app/dist/vue-app /usr/share/nginx/html
COPY frontend/vue-app/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
