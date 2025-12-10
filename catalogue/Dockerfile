FROM node:20.19.5-alpine3.21 AS BUILD
WORKDIR /opt/server
EXPOSE 8080/tcp
COPY package.json .
COPY *.js .
RUN npm install


FROM node:20.19.5-alpine3.21 AS FINAL
RUN addgroup -S roboshop adduser -S roboshop -G roboshop
WORKDIR /opt/server
COPY --from=BUILD /opt/server /opt/server
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
RUN chown -R roboshop:roboshop /opt/server
USER roboshop
CMD ["server.js"]
ENTRYPOINT ["node"]





# WORKDIR /opt/server
# EXPOSE 8080/tcp
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO=true \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["node", "server.js"]