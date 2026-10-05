# Mission Reflection

Writing a `docker-compose.yml` file makes a cloud engineer's job easier because it allows the configuration of multiple containers to be written in one organized file. Instead of manually typing several Docker commands every time, the engineer can use `docker-compose up -d` to deploy the complete application stack. This also makes the deployment easier to repeat and share with other engineers.

YAML is very sensitive to indentation, so an indentation error can cause the Compose file to become invalid. For example, using a Tab instead of spaces or placing a line at the wrong indentation level may cause Docker Compose to report a YAML parsing error. This taught me that proper formatting is important when creating infrastructure configuration files.

Environment variables such as `MYSQL_PASSWORD`, `MYSQL_DATABASE`, and `MYSQL_USER` were used to provide configuration information to the containers. They allow the application and database containers to know which credentials and database settings to use. Environment variables also make the configuration more flexible because values can be changed without modifying the application itself.

Deploying Nextcloud in only a few minutes was a useful experience because it showed me how cloud technologies can simplify the deployment of complex systems. Instead of manually installing a web server, database server, and other components, Docker Compose allowed the entire infrastructure to be created from a single configuration file.

Since Mission 1, my understanding of Cloud Computing has evolved from simply learning about cloud concepts to actually deploying and managing cloud infrastructure. I have learned how Linux, Docker, containers, networking, storage, databases, and application services work together. This laboratory helped me understand that cloud engineers need both technical skills and good documentation practices to create reliable and repeatable deployments.
