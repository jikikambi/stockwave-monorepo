# Stage 1: Build Angular app
FROM node:20 AS build
WORKDIR /usr/src/app

COPY package*.json ./
COPY nx.json ./
COPY tsconfig.base.json ./
COPY eslint.config.mjs ./ 

# Install dependencies
RUN npm install --legacy-peer-deps

COPY . .

# Build the Angular app using Nx
RUN npx nx build angular-app --prod

# Stage 2: Serve with Nginx
FROM nginx:alpine
COPY --from=build /usr/src/app/dist/angular-app /usr/share/nginx/html
COPY frontend/angular-app/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
