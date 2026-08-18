1. Compute Resources
Example
The compute resource available in the KillerCoda Linux environment is the virtual CPU (vCPU) and RAM.

Purpose
Compute resources provide the processing power and memory needed to run commands, applications, and processes.

Importance in Cloud Computing
Compute resources are important because cloud applications require CPU and memory to operate. Cloud providers provide virtual compute resources that can be increased or decreased depending on the workload.

Relation to KillerCoda
The KillerCoda Ubuntu environment provides virtual CPU and memory resources for running Linux commands and applications. I used the following commands to check the available compute resources.using lscpu, free -h command.

2. Storage Resources
Example

The storage resource is the virtual disk or filesystem provided to the Ubuntu Linux environment.

Purpose

Storage resources are used to store operating system files, applications, configuration files, user files, and other data.

Importance in Cloud Computing

Storage is important because cloud applications need a place to save data. Cloud storage allows data to be stored and accessed without requiring users to maintain physical storage devices.

Relation to the KillerCoda Linux Environment

The KillerCoda Ubuntu environment provides a filesystem where files and directories can be created and stored. The available disk space can be examined using the df -h command.

3. Networking Resources
Example

The networking resource is the virtual network interface and IP address assigned to the Linux environment.

Purpose

Networking allows the Linux environment to communicate with other computers, servers, and Internet services.

Importance in Cloud Computing

Networking is important because cloud resources must communicate with users, applications, databases, and other cloud services. A reliable network allows users to access cloud applications and services remotely.

Relation to the KillerCoda Linux Environment

The KillerCoda Linux environment uses networking to communicate with external services and the Internet. Network information can be checked using commands such as: ip addr

4. Operating System
Example

The operating system used in the KillerCoda environment is Ubuntu Linux.

Purpose

The operating system manages computer resources and provides an environment where applications and commands can run.

Importance in Cloud Computing

The operating system is important because cloud servers need an operating system to manage computing resources, storage, networking, users, processes, and applications.

Relation to the KillerCoda Linux Environment

KillerCoda provides Ubuntu-based Linux environments for learning and practicing technologies. The Ubuntu environment allows users to execute Linux commands, manage files, inspect system resources, and perform cloud-related activities.

The operating system information can be checked using:
uname -a or cat /etc/os-release
