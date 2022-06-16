FROM dockerhub.ir/python:3.8-slim-buster

WORKDIR /app

RUN groupadd -g 1000 app && useradd -u 1000 -g app -m app && \
    chown app:app /app && \
    apt-get update && \
    apt-get install -y gcc libjpeg-dev zlib1g-dev && \
    rm -rf /var/cache/apt/archives /var/lib/apt/lists/*

USER app

COPY --chown=app:app ["requirements.txt", "/app/"]
RUN pip install -r requirements.txt

COPY --chown=app:app [".", "/app/"]

ENV PATH="/home/app/.local/bin:${PATH}"

ENTRYPOINT ["uwsgi", "--module", "core.wsgi:application"]
