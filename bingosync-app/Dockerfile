FROM python:3.7-bullseye

# Note: bingosync uses the 'node' command, this means we need to install node
RUN apt-get update && apt-get install -y \
    software-properties-common \
    npm
RUN npm install npm@latest -g && \
    npm install n -g && \
    n latest


RUN mkdir app
WORKDIR /app
ADD ./requirements.txt requirements.txt
COPY . .
RUN sed -i "s/YOUR_PUBLIC_DOMAIN/$(curl -s https://ipinfo.io/ip)/" bingosync/settings.py
RUN pip install -r requirements.txt
EXPOSE 8000
