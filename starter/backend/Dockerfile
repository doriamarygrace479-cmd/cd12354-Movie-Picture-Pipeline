FROM python:3.10-slim

ENV FLASK_RUN_HOST=0.0.0.0
ENV PIP_NO_CACHE_DIR=1
ENV PIPENV_NOSPIN=1

WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    gcc \
    python3-dev \
    libpcre2-dev \
    libffi-dev \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir pipenv

COPY Pipfile Pipfile.lock /app/

RUN pipenv install --system --deploy

COPY . /app

EXPOSE 5000

CMD ["pipenv", "run", "serve"]
