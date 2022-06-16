FROM dockerhub.ir/node:14.19.3-buster-slim

WORKDIR /app

RUN groupadd -g 2000 app && useradd -u 2000 -m -g app app && \
    chown app:app /app

USER app

COPY --chown=app:app ["package.json", "/app/"]
RUN npm install

COPY --chown=app:app [".", "/app/"]
RUN npm run build

CMD ["npm", "start"]
