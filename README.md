
## Overview

Reminder Service manages CRUD operations on the reminder entity. Clients can interact with API endpoints provided by this service to perform these operations. 

- This service interfaces with PostgreSQL database to store the reminders created by various users. 
- The most recent state of the reminder entity is maintained in the reminders database. 
- All the operations that are being performed on the reminder entity by the user are packed as an event-object and published to an AWS SNS topic which then forwards the event-message to the AWS.

#### Prerequisites

- Make sure you have
    - Installed Docker (when running using docker)
    - PostgreSQL ```reminders-database``` running and is accessible using host-url, username and password
    - AWS SNS ```event-topic``` setup and is accessible using ARN

#### Using Docker

- In source directory ```src/``` run the following command
	- ```$ yarn install``` - install required dependencies
	- ```$ yarn build``` - build source code
	- ```$ yarn test``` - run test (optional)
	- ```$ docker build -t reminder-service .``` - build docker image
- With successful execution of above commands you will have a docker-image for the reminder-service
- The docker-image can be run using the following command
    - ```docker run -p 3000:3000 --env-file ./.env reminder-service```
- On successful start, the API documentaion (built using Swagger) for the service will be accssible on ```http://<DOCKER_HOST>:3000/docs```

#### Without Docker

- Replace the env-variables at ```/src/src/common/api-config.service.ts```
- Use the following commands to start the service
    - ```$ yarn install``` - install required dependencies
    - ```$ yarn test``` - run test (optional)
    - ```$ yarn start``` - start reminder-service
- On successful start, the API documentaion (built using Swagger) for the service will be accssible on ```http://localhost:3000/docs```

## CI/CD and Deployment Guide

A brief description of the deployment strategy is described in [documentation of continuous-improvement project](https://continuous-improvement.readthedocs.io).

## Contributing

There are multiple ways to contribute to this project, read about them [here](https://continuous-improvement.readthedocs.io/en/latest/md/community/contributing.html).

## License

All versions of the app are open-sourced, read more about this [LICENSE](https://github.com/adisakshya/reminder-service/blob/master/LICENSE).
