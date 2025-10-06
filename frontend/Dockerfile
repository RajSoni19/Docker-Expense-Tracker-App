
FROM node:22-slim AS builder
WORKDIR /app


COPY package*.json ./
RUN npm ci


ARG REACT_APP_API_URL=/api
ENV REACT_APP_API_URL=${REACT_APP_API_URL}

COPY . .
RUN npm run build


FROM nginx:alpine

RUN rm -rf /usr/share/nginx/html/*


COPY --from=builder /app/build /usr/share/nginx/html

# Copy a custom nginx config to enable SPA routing + proxy /api -> backend
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
