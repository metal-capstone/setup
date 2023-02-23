# Spotify Chatbot Setup Instructions

## Install

- Docker Desktop (<https://www.docker.com/products/docker-desktop/>)
- Git

## Setup

Start docker desktop and wait until docker is running (the docker whale in the bottom left will be green), and then run these commands in the folder you want to install the api and app:

```git
mkdir spotify-chatbot
cd spotify-chatbot
git clone https://github.com/metal-capstone/setup.git
git clone https://github.com/metal-capstone/app.git
git clone https://github.com/metal-capstone/api.git
```

After that go to the shared google drive folder and download `credentials.json` and place it in the `/api` folder. This is needed to access the other APIs that are used. Finally you can navigate to the setup folder and run the app and api by running:

```docker
cd setup
docker compose up
```

After that the React App should be running on localhost:3000 and the API should be running on localhost:8000. Press ctrl+c to stop the containers.

## Development

Make sure docker desktop is running and then run `docker compose up` in the setup folder to start the app and api after setup. Any saved changes should auto reload the app or api without needing a restart.

## How to Debug API

Make sure docker desktop is running. Open the `/setup` folder. Run `docker compose -f docker-compose.debug.yaml up`. Wait for docker compose to finish starting containers. Open the `/api` folder in vscode. Click the `Run and Debug` tab on the left drawer of vscode. Place breakpoints where you wan them in the api. Select `Python: Start and attach to API`. Click the green play button.

## How to Debug APP

Make sure docker desktop is running. Open the `/setup` folder. Run `docker compose up`. Wait for docker compose to finish starting containers. Open the `/app` folder in vscode. Click the `Run and Debug` tab on the left drawer of vscode. Place breakpoints where you wan them in the app. Select `Launch Chrome: React App Debugging`. Click the green play button.

## Adding packages

When adding packages to either the app or api, you must rebuild the docker images or you will encounter issues when trying to use any new packages.

**NOTE:** If you are checking out someone elses code and they have new packages you will have to rebuild either the app or api images.

### App (npm)

Make sure the containers are stopped by pressing ctrl+c in the terminal. Navigate to the app folder and run `npm i <package>` for whatever package you want to add, and then run these commands to delete the old docker image:

```docker
docker rm setup-app-1
docker image rm setup-app
```

After that navigate back to the setup folder and run `docker compose up` which will rebuild the image with the proper packages

### API (pip)

Make sure the containers are stopped by pressing ctrl+c in the terminal. Open the API folder and add the package you want to the `requirement.txt` file, and then run these commands to delete the old docker image:

```docker
docker rm setup-api-1
docker image rm setup-api
```

After that make sure you are in the setup folder and run `docker compose up` which will rebuild the image with the proper packages.
