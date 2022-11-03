# install dependencies
FROM node:16 AS InstallationStage
WORKDIR /sales-system/client
COPY . .
RUN npm install
RUN npm run build
RUN npm prune --production

# serve
FROM node:16 AS AppStage
WORKDIR /sales-system/client
EXPOSE 3000
COPY --from=InstallationStage /sales-system/client/node_modules ./node_modules
COPY --from=InstallationStage /sales-system/client/.next ./.next
CMD [ "npm", "start" ]