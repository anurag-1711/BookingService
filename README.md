# Booking Service

## Description

This README file provides an overview and instructions for using the booking service in your personal airline management system project. The booking service is responsible for handling flight bookings and related operations.

## Table of Contents

- [Introduction](#introduction)
- [Dependencies](#dependencies)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Error Handling](#error-handling)
- [Message Queue](#message-queue)
- [Model Definition](#model-definition)
- [Technologies Used](#technologies-used)
- [Contributing](#contributing)

## Introduction

The booking service is a part of the airline management system project and provides functionality to create flight bookings, check seat availability, and update booking status. It interacts with a MySQL database for data persistence and RabbitMQ as a message broker for publishing notifications. This service is built using Node.js and Express.js.

## Dependencies

The following dependencies are required to run the booking service:

- Node.js
- Express.js
- MySQL
- RabbitMQ

Please make sure you have these dependencies installed before proceeding with the installation.

## Installation

To install and set up the booking service, follow these steps:

1. Clone the project repository to your local machine.
2. Navigate to the project directory.
3. Install the dependencies by running the following command:

   ```bash
   npm install
   ```

4. Set up the MySQL database and update the database configuration in the project files as described in the [Configuration](#configuration) section.
5. Set up RabbitMQ and update the message broker configuration in the project files as described in the [Configuration](#configuration) section.

## Configuration

Before running the booking service, you need to configure the database connection and the message broker settings. Follow these steps to configure the service:

### Database Configuration

Create a config.json file in the `config` directory and add the following code to it with your MySQL username and password:

```
    {
        "development": {
            "username": <YOUR_USERNAME>,
            "password": <YOUR_PASSWORD>,
            "database": "BOOKING_DB_DEV",
            "host": "127.0.0.1",
            "dialect": "mysql"
        }
    }

```

### Message Broker Configuration (RabbitMQ)

1. Open the `config/serverConfig.js` file.
2. Update the `MESSAGE_BROKER_URL`, `EXCHANGE_NAME` variables with your RabbitMQ server URL and exchange name.

## Usage

To start the booking service, run the following command in the project directory:

```bash
npm start
```

The service will start on the specified port and listen for incoming requests.

## API Endpoints

The booking service provides the following API endpoints:

- **POST /bookings**: Create a new booking by providing flight and user details. Returns the created booking information.
- **POST /publish**: Publish a message to the message queue for notification purposes. Returns a success message.

Refer to the source code in the `routers/router.js` file for more details on the API endpoints and their corresponding controller methods.

## Error Handling

The booking service implements custom error classes for different types of errors. The error classes are defined in the `utils/errors` folder. These classes include:

- `AppError`: Represents a generic application error.
- `ServiceError`: Represents a service-specific error.
- `ValidationError`: Represents a validation error.

The service handles errors gracefully and returns appropriate error responses to the client.

## Message Queue

The booking service uses RabbitMQ as a message broker for publishing notifications. The `utils/messageQueue.js` file contains the necessary functions for creating a channel, subscribing to messages, and publishing messages. The message queue configuration can be updated in the `config/serverConfig.js` file.

## Model Definition

The booking service uses a Sequelize model to define the `Booking` entity. The model definition can be found in the `models/Booking.js` file. It includes attributes such as `flightId`, `userId`, `status`, `noOfSeats`, and `totalCost`.

## Technologies Used

The booking service is built using the following technologies and frameworks:

- Node.js: JavaScript runtime environment.
- Express.js: Web application framework for Node.js.
- MySQL: Relational database for data persistence.
- RabbitMQ: Message broker for publishing notifications.

## Contributing

Contributions to the airline management system project are welcome. If you have any suggestions, bug reports, or feature requests, please open an issue or submit a pull request on the project repository.
