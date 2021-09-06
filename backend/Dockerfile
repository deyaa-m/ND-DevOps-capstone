From node:13.8-alpine3.11

WORKDIR /app
COPY . .
RUN echo ENVIRONMENT=production > .env \
    &&  cat .env.sample >> .env \
    &&  npm i && npm install -g npm-check-updates \
    &&  ncu -u standard-version && npm i standard-version@7 \
    &&  npm run build

ENV NODE_ENV=production
ENV ENVIRONMENT=production
ENV TYPEORM_HOST=capstone.cvoqi16sdmf6.eu-west-2.rds.amazonaws.com
ENV TYPEORM_PORT=5432
ENV TYPEORM_USERNAME=postgres
ENV TYPEORM_PASSWORD=postgresadmin
ENV TYPEORM_DATABASE=capstone

EXPOSE 3030

CMD ["npm", "run", "start"]
 