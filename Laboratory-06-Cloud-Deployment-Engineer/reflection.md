# Mission Reflection

In this laboratory, I learned how Docker Compose can make a cloud engineer's work easier. Instead of manually typing many Docker commands to create and configure each container, I can put all the required settings inside a `docker-compose.yml` file. After creating the file, I only need to run `docker-compose up -d` to start the different services. This makes the deployment faster, more organized, and easier to repeat.

I also learned that YAML files are very sensitive to indentation. If I accidentally use a Tab instead of spaces or put something at the wrong indentation level, Docker Compose may not be able to read the file correctly. It can result in an error and prevent the containers from starting. Because of this, I realized that even small formatting mistakes can affect the whole deployment.

We used environment variables such as `MYSQL_PASSWORD`, `MYSQL_DATABASE`, and `MYSQL_USER` because the containers need configuration information to communicate with each other. These variables tell MariaDB and Nextcloud which database, username, and password to use. I also learned that `MYSQL_HOST=database` allows Nextcloud to find the MariaDB container using its service name.

Deploying Nextcloud in only a few minutes was exciting because I was able to see how powerful Docker can be. At first, the process looked complicated, but after following the steps, I was able to deploy the application and database containers successfully. Seeing the Nextcloud setup page appear in the browser made me feel that I was actually doing a real cloud deployment.

Since Mission 1, my understanding of Cloud Computing has improved a lot. I now understand that cloud computing is not only about storing files online. I have learned how Linux, Docker, containers, databases, networking, and applications can work together to create a working cloud system. This laboratory also helped me become more confident in using command-line tools and managing cloud infrastructure.
