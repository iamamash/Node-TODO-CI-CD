# Node.js Application

## Description
This is a Node.js application that can be deployed using various methods: npm, Docker Compose, and Kubernetes.

## Deployment Methods

### 1. Running via npm

To run the application directly via npm, follow these steps:

1. Install Node.js and npm if they are not already installed:
    ```bash
    sudo apt install nodejs
    sudo apt install npm
    ```

2. Install the application dependencies:
    ```bash
    npm install
    ```

3. Start the application:
    ```bash
    node app.js
    ```

### 2. Running via Docker Compose

To run the application using Docker Compose, execute the following command:

```bash
docker-compose up -d
```

### 3. Running via Kubernetes (using Minikube)

To deploy the application on Kubernetes using Minikube, follow these steps:

1. Apply the Kubernetes configuration:
    ```bash
    kubectl apply -f K8s/
    ```

2. Forward the service port to access the application:
    ```bash
    kubectl port-forward service/node-app-service --address 0.0.0.0 30007:80
    ```

3. (Optional) To deploy `hpa.yaml`, first install [ngrok](https://ngrok.com/), then run the following commands:
    ```bash
    minikube ip
    ngrok http <minikube-ip>:30007
    ```

    Update the URL provided by ngrok in the `host:` field of `hpa.yaml`, and reapply it:
    ```bash
    kubectl apply -f hpa.yaml K8s/
    ```

4. Access the application using the ngrok URL.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Thanks to the contributors who made this project possible.
- [Node.js](https://nodejs.org/) - JavaScript runtime built on Chrome's V8 JavaScript engine.
- [Docker Compose](https://docs.docker.com/compose/) - Tool for defining and running multi-container Docker applications.
- [Kubernetes](https://kubernetes.io/) - Open-source system for automating deployment, scaling, and management of containerized applications.
- [Minikube](https://minikube.sigs.k8s.io/docs/) - Tool to run Kubernetes locally.
- [ngrok](https://ngrok.com/) - Tool to create secure tunnels to your localhost.

```

Feel free to adjust any sections as needed!
