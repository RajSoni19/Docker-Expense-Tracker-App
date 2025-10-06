
FROM node:22-slim


WORKDIR /usr/src/app

COPY package*.json ./
RUN npm ci --only=production


COPY . .


USER node

ENV NODE_ENV=production
EXPOSE 5000

# adapt entrypoint if your app uses "npm start"
CMD ["node", "server.js"]
# OR if your repo uses `npm start` script: CMD ["npm", "start"]
