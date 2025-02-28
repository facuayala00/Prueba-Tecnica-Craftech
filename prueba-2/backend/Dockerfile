# pull official base image
FROM python:3.9-alpine

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# install dependencies
RUN pip install --upgrade pip
COPY requirements.txt .
RUN apk add --update --no-cache postgresql-client
# install temp dependencies for build of pyscopg2 etc
RUN apk add --update --no-cache --virtual .tmp-build-deps \
    gcc \
    musl-dev \
    postgresql-dev \
    && pip install --no-cache-dir -r requirements.txt \
    && apk del --no-cache .tmp-build-deps

# copy entrypoint.sh and make it executable
COPY entrypoint.sh .
RUN chmod +x entrypoint.sh

# copy project files
COPY . .

# Expose port
EXPOSE 8000

# run entrypoint.sh
ENTRYPOINT ["sh", "/usr/src/app/entrypoint.sh"]
