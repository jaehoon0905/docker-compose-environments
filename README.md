# **Multi-Environment Docker Compose Configurations**

This repository contains Docker Compose configurations for multiple environments and services. It aims to provide a consistent and reproducible way to set up development, testing, staging, and production environments for different applications using Docker Compose. The configurations are structured to support various environments while minimizing redundancy and ensuring scalability.

---

## **How to Use**

### **Prerequisites**
Before running the Docker Compose configurations, ensure the following prerequisites are met:

- **Docker**
- **Docker Compose**
- **Git**: To clone the repository.

### **Setup Instructions**

1. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/jaehoon0905/docker-compose-environments.git
   cd docker-compose-environments
   ```

2. Navigate to the appropriate environment directory or use the common configuration files as needed.

3. Copy the `.env.example` file to `.env`:
   ```bash
   cp .env.example .env
   ```

4. Modify the `.env` file to suit your local configuration (e.g., database credentials, API keys).

### **Running Services**

To bring up the services for a specific environment, use the following command within the environment's directory:

```bash
docker-compose up
```

This command will build the containers, start the services, and run them in the background. You can use the `-d` flag to run the services in detached mode:

```bash
docker-compose up -d
```

To stop and remove the containers, use:

```bash
docker-compose down
```

For more advanced configurations (e.g., scaling services, running in different networks), refer to the individual `docker-compose.yml` files.

---

## **Configuration Files**

### **docker-compose.yml**

This is the primary configuration file for each environment. It defines the services, networks, volumes, and build contexts for your containers. Each environment may override certain sections to suit its needs.

### **docker-compose.override.yml**

If you need to make environment-specific changes (e.g., enabling debugging or exposing different ports), you can use an override file. For example, in the development environment, you might use this file to expose different ports for local development.

### **.env Files**

Each environment contains a `.env` file that holds sensitive configuration data such as database credentials, API keys, or environment-specific variables. This helps separate configuration from the actual Docker setup and enables easier updates to sensitive information.

---

## **Best Practices**

- **Environment Isolation**: Keep environment configurations separate to avoid accidental conflicts. Always use `.env` files to manage sensitive data and environment-specific variables.
- **Version Control**: Keep Docker Compose configurations and associated files under version control to track changes across environments.
- **Minimize Redundancy**: Use common configuration files for shared services like databases and caches. Override specific settings for each environment as needed.
- **Security**: Never commit sensitive data such as passwords, secret keys, or tokens in the repository. Always use `.env` files or other secure methods to handle sensitive configurations.

---
