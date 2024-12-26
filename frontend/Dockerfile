

FROM node:20 as build

WORKDIR /app

# Clear npm cache and install dependencies
RUN npm cache clean --force
COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build --prod

FROM nginx:1.25
COPY --from=build /app/dist/project/browser /usr/share/nginx/html
COPY nginx.conf /etc/nginx/nginx.conf
EXPOSE 8080
CMD ["nginx", "-g", "daemon off;"]



