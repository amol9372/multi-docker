# FROM node:alpine as builder

# USER node

# RUN mkdir -p /home/node/app

# WORKDIR /home/node/app

# COPY --chown=node:node ./package.json ./

# RUN npm install

# COPY --chown=node:node ./ ./

# CMD ["npm", "run", "build"]

# # Nginx configuration

# FROM nginx

# EXPOSE 3000

# COPY ./nginx/default.conf /etc/nginx/conf.d/ 

# COPY --from=builder /home/node/app/build /usr/share/nginx/html/

# Build frontend code
FROM node:alpine as builder

WORKDIR '/app'

COPY package.json .

RUN npm install

COPY . .

RUN npm run build


# Run nginx
# This will also start nginx
FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/

COPY --from=builder /app/build /usr/share/nginx/html