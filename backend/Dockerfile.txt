FROM node:18-alpine


WORKDIR /usr/src/app


# install dependencies
COPY backend/package*.json ./
RUN npm install --production


# copy source
COPY backend/ ./


ENV PORT=8080
EXPOSE 8080
CMD ["node", "server.js"]