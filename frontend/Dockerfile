From node:13.8-alpine3.11 AS builder

WORKDIR /app

COPY . .

# to bake the code with backend url
## backend is the cluster's service for backend deployment
## you are free to use any other value while building
## by using the flag --build-arg IP=<value>
ARG IP=backend-service
ENV API_URL=http://${IP}:3030

run echo ${API_URL}
RUN npm i && npm audit fix \
    && npm run build --production

From nginx 
#node:13.8-alpine3.11 

WORKDIR /app

COPY --from=builder /app/dist /app
COPY nginx-default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80 3000

#CMD ["npm", "run", "start"]