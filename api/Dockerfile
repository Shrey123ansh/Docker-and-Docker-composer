# FROM node:17-alpine

# WORKDIR /app

# COPY . .

# RUN npm install

# EXPOSE 4000
# # required for docker desktop port mapping

# CMD ["node", "app.js"]


# FROM node:17-alpine

# WORKDIR /app
# working directory

# COPY package.json .

# RUN npm install

# COPY . . 
# #source code copy

# EXPOSE 4000
# # required for docker desktop port mapping

# CMD ["node", "app.js"]

FROM node:17-alpine

RUN npm install -g nodemon

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .
# #source code copy

EXPOSE 4000
# required for docker desktop port mapping

CMD ["npm", "run", "dev"]