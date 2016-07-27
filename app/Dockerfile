# FROM evild/alpine-python:3.5
FROM python:3-slim

ENV PYTHONUNBUFFERED=TRUE

# Install system dependencies
RUN apt-get update && \
    apt-get install -y \
        libpq-dev \
        gcc && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN mkdir -p /app/
WORKDIR /app

ADD ./requirements.txt /app/
RUN pip install -r /app/requirements.txt

COPY . /app

EXPOSE 8001
# CMD gunicorn app --bind 0.0.0.0:8000 --log-level debug --reload
CMD python manage.py runserver 0.0.0.0:8001
