# Spotify Chatbot Setup Instructions

## Install

- Docker Desktop (https://www.docker.com/products/docker-desktop/)
- Git

## Setup

Run these commands in the folder you want to install the chatbot:
```
mkdir spotify-chatbot
cd spotify-chatbot
git clone https://github.com/metal-capstone/setup.git
git clone https://github.com/metal-capstone/app.git
git clone https://github.com/metal-capstone/api.git
cd setup
docker compose up
```
After that the API and React App should be running on localhost:3000 and localhost:8000. Press ctrl+c to stop the containers.

## Development

Run `docker compose up` in the setup folder to start the app and api after setup.
