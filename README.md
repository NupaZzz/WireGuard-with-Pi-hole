# WireGuard with Pi-hole

This repository contains a Vagrant configuration file and a Docker Compose file for setting up a test environment with WireGuard and Pi-hole.

The Vagrantfile is used to create a virtual machine as a test environment using the ubuntu/focal64 box. It assigns a static IP address to the VM, sets up folder forwarding, and forwards several ports from the host to the guest VM. It also provisions the VM to install Docker and Docker Compose, and then runs docker-compose up in the /vagrant directory.

The docker-compose.yml file defines two services: WireGuard and Pi-hole. Both services are configured with specific network settings, environment variables, and volume mounts. They are also assigned static IP addresses within a custom Docker network. The WireGuard service is configured to use Pi-hole as its DNS server.

Please note that you should replace the placeholder values in the docker-compose.yml file with your actual values before running these configurations. For example, you should replace 'your-password' with your actual Pi-hole web interface password. Also, ensure that the static IP addresses assigned to the services do not conflict with any other devices in your network. This setup is intended for testing purposes and may need to be adjusted for production environments.
