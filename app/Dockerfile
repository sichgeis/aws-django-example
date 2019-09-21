FROM python:3.7.2-alpine3.9

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

RUN apk update
RUN apk add python3-dev postgresql-dev gcc linux-headers libc-dev

WORKDIR /usr/src/app/

RUN pip install pipenv
COPY Pipfile Pipfile.lock ./
RUN pipenv install --system

COPY . .

ENTRYPOINT ["/usr/src/app/entrypoint.sh"]