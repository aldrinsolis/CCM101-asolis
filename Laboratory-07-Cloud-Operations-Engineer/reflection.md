
# Laboratory 07 – Mission Reflection

During this laboratory, I learned how important monitoring is in cloud operations. I used Linux commands and Docker tools to check system resources, deploy a web server, generate requests, and investigate application activity.

First, checking the host server's resources is important even when containers are running perfectly because containers still depend on the host's CPU, RAM, and disk space. If the server runs out of memory or storage, applications may become slow, crash, or stop working. Monitoring the host helps engineers identify resource problems before they affect users.

Second, the `docker logs` command helps troubleshoot a user who cannot log in to a web application. By examining the logs, an engineer can look for failed requests, error messages, and other clues that explain what happened. These details help narrow down the possible cause instead of guessing. However, authentication problems may require additional application or security logs.

Third, logs and metrics provide different types of information. Logs record events, requests, and errors that happen inside an application. Metrics provide numerical measurements, such as CPU percentage, memory usage, and network traffic. Both are important because logs explain individual events while metrics help identify performance problems and unusual resource consumption.

Fourth, large enterprise companies can monitor thousands of containers using centralized monitoring systems. Tools such as Prometheus collect and store metrics, while Grafana displays dashboards and visualizations. These systems can also use alerts to notify engineers when resource usage becomes unusually high or an application becomes unhealthy.

Finally, this laboratory improved my ability to troubleshoot Linux environments. I practiced checking RAM and disk space, observing running processes, deploying Docker containers, testing HTTP requests, and reading application logs. I also learned how to monitor container resource usage through Docker stats. These activities helped me understand that maintaining a reliable application requires continuous monitoring, careful investigation, and proper documentation.

