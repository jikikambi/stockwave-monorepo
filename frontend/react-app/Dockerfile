# Stage 1: Build React app
FROM node:20 AS build
WORKDIR /usr/src/app

COPY package*.json ./
COPY nx.json ./
COPY tsconfig.base.json ./
COPY eslint.config.mjs ./ 

RUN npm install --legacy-peer-deps

COPY . .

# Build the React app using Nx
RUN npx nx build react-app --prod

# Stage 2: Serve with Nginx
FROM nginx:alpine
COPY --from=build /usr/src/app/dist/react-app /usr/share/nginx/html
COPY frontend/react-app/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
