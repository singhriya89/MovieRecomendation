<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <h1>Movie Recommendation System</h1>
    <p><strong>Note:</strong> This project is a work in progress and is not yet ready for production use. It is actively being developed and may undergo significant changes. Contributions and suggestions are welcome!</p>
    <h2>Overview</h2>
    <p>The Movie Recommendation System is a Java-based project built with <a href="https://spring.io/projects/spring-boot">Spring Boot</a> (version 2.3.4) and <a href="https://www.mysql.com/">MySQL</a> (version 8.0). It provides a platform where users can:</p>
    <ul>
        <li>Register and create a profile</li>
        <li>Rate movies</li>
        <li>Receive personalized movie recommendations based on their preferences</li>
    </ul>
    <h2>Features</h2>
    <table>
        <thead>
            <tr>
                <th>Feature</th>
                <th>Status</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>User Registration</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>Movie Database</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>Rating System</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>Recommendation Algorithm</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>User Interface</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>Search Functionality</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>Top Rated Movies</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>User Profile</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>Data Persistence</td>
                <td>In Progress</td>
            </tr>
            <tr>
                <td>Error Handling</td>
                <td>In Progress</td>
            </tr>
        </tbody>
    </table>
    <p><img src="https://img.shields.io/badge/Status-In%20Progress-yellow" alt="Status"></p>
    <h2>Prerequisites</h2>
    <ul>
        <li><strong>Java 11</strong>: Ensure you have <a href="https://www.oracle.com/java/technologies/downloads/#java11">Java 11</a> installed on your system.</li>
        <li><strong>Docker Desktop</strong>: Download and install <a href="https://www.docker.com/">Docker Desktop</a>.</li>
        <li><strong>MySQL 8.0</strong>: Use the <a href="https://dev.mysql.com/downloads/installer/">MySQL Installer</a> to install MySQL.</li>
        <li><strong>Maven</strong>: Install Maven for dependency management.</li>
    </ul>
    <h2>Installation</h2>
    <h3>Step 1: Clone the Repository</h3>
    <pre><code>git clone https://github.com/singhriya89/MovieRecomendation.git</code></pre>
    <h3>Step 2: Configure the MySQL Container</h3>
    <p>Update the <code>docker-compose-mysql.yml</code> file with your desired MySQL root password:</p>
    <pre><code>version: '3.8'

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
</code></pre>
    <p>Start the MySQL container:</p>
    <pre><code>cd /path/to/MovieRecommendationSystem
docker-compose -f docker-compose-mysql.yml up -d</code></pre>
    <h3>Step 3: Update Database Configuration</h3>
    <p>Edit <code>src/main/resources/application-default.properties</code> with your MySQL credentials:</p>
    <pre><code>spring.datasource.url=jdbc:mysql://127.0.0.1:3308/movie_recommendation
spring.datasource.username=root # Replace with your username
spring.datasource.password=yourpassword # Replace with your password
spring.jpa.hibernate.ddl-auto=update
server.port=8080</code></pre>
    <h3>Step 4: Install Maven Dependencies</h3>
    <pre><code>cd MovieRecommendationSystem
mvn install</code></pre>
    <h3>Step 5: Download and Extract MovieLens Dataset</h3>
    <p>Run the following command to download and extract the MovieLens dataset:</p>
    <pre><code>if [ ! -d "src/main/resources/data/ml-25m" ]; then \
  curl -O https://files.grouplens.org/datasets/movielens/ml-25m.zip && \
  unzip ml-25m.zip -d src/main/resources/data/ && \
  rm ml-25m.zip; \
fi</code></pre>
    <p>If you're on Windows without Git Bash, download Git Bash from <a href="https://git-scm.com/downloads">here</a>.</p>
    <h3>Step 6: Build and Run the Application</h3>
    <pre><code>mvn spring-boot:run</code></pre>
    <h3>Step 7: Load Default Movie Data</h3>
    <p>Use Postman or a terminal to send a POST request to load default movie data:</p>
    <pre><code>curl -X POST http://localhost:8080/loadDefaultMovies</code></pre>
    <p>Or on Windows PowerShell:</p>
    <pre><code>Invoke-WebRequest -Method POST -Uri http://localhost:8080/loadDefaultMovies</code></pre>
    <h2>Contributing</h2>
    <p>Contributions are welcome! If you find any issues or have suggestions for improvement, feel free to submit a pull request.</p>
    <h2>License</h2>
    <p>This project is licensed under the MIT License. See the <a href="LICENSE">LICENSE</a> file for details.</p>
</body>
</html>
