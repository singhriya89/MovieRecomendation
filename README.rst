Movie Recommendation System



Note: This project is a work in progress and is not yet ready for production use. It is actively being developed and may undergo significant changes. Contributions and suggestions are welcome!

Overview

The Movie Recommendation System is a Java-based project built with Spring Boot (version 2.3.4) and MySQL (version 8.0). It provides a platform where users can:

Register and create a profile

Rate movies

Receive personalized movie recommendations based on their preferences

Features

Feature

Status

User Registration

In Progress

Movie Database

In Progress

Rating System

In Progress

Recommendation Algorithm

In Progress

User Interface

In Progress

Search Functionality

In Progress

Top Rated Movies

In Progress

User Profile

In Progress

Data Persistence

In Progress

Error Handling

In Progress



Prerequisites

Java 11: Ensure you have Java 11 installed on your system.

Docker Desktop: Download and install Docker Desktop.

MySQL 8.0: Use the MySQL Installer to install MySQL.

Maven: Install Maven for dependency management.

Installation

Step 1: Clone the Repository

git clone https://github.com/singhriya89/MovieRecomendation.git

Step 2: Configure the MySQL Container

Update the docker-compose-mysql.yml file with your desired MySQL root password:

version: '3.8'

services:
  localmysql:
    container_name: db
    restart: always
    image: 'mysql'
    environment:
      MYSQL_DATABASE: 'movie_recommendation'
      MYSQL_ROOT_PASSWORD: yourpassword # Replace with your password
    ports:
      - 3308:3306

Start the MySQL container:

cd /path/to/MovieRecommendationSystem
docker-compose -f docker-compose-mysql.yml up -d

Step 3: Update Database Configuration

Edit src/main/resources/application-default.properties with your MySQL credentials:

spring.datasource.url=jdbc:mysql://127.0.0.1:3308/movie_recommendation
spring.datasource.username=root # Replace with your username
spring.datasource.password=yourpassword # Replace with your password
spring.jpa.hibernate.ddl-auto=update
server.port=8080

Step 4: Install Maven Dependencies

cd MovieRecommendationSystem
mvn install

Step 5: Download and Extract MovieLens Dataset

Run the following command to download and extract the MovieLens dataset:

if [ ! -d "src/main/resources/data/ml-25m" ]; then \
  curl -O https://files.grouplens.org/datasets/movielens/ml-25m.zip && \
  unzip ml-25m.zip -d src/main/resources/data/ && \
  rm ml-25m.zip; \
fi

If you're on Windows without Git Bash, download Git Bash from here.

Step 6: Build and Run the Application

Build and run the application using Maven:

mvn spring-boot:run

Step 7: Load Default Movie Data

Use Postman or a terminal to send a POST request to load default movie data:

curl -X POST http://localhost:8080/loadDefaultMovies

Or on Windows PowerShell:

Invoke-WebRequest -Method POST -Uri http://localhost:8080/loadDefaultMovies

Contributing

Contributions are welcome! If you find any issues or have suggestions for improvement, feel free to submit a pull request.

License

This project is licensed under the MIT License. See the LICENSE file for details.

