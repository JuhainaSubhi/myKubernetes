# Redis Kubernetes Deployment

This repository contains Kubernetes configuration for deploying a Redis server.

## Contents

- `pod.yml`: Defines a Pod running a Redis server.
- `README.md`: This file with deployment instructions.

## Deployment Instructions

Follow these steps to deploy Redis using Kubernetes:

### 1. **Clone the Repository**

First, you need to clone the repository to your local machine. This involves copying the repository from GitHub to your local environment.

### 2. **Create the Redis Pod**

To set up the Redis Pod:

1. **Create the `pod.yml` File:**

   The `pod.yml` file defines the configuration for the Redis Pod. This file specifies the Redis container image and the port it will use. Ensure this file is properly configured and available in the repository.

2. **Deploy the Redis Pod:**

   Apply the configuration defined in `pod.yml` to create the Redis Pod in your Kubernetes cluster. This step involves using Kubernetes commands to apply the configuration and create the Pod based on the file.

3. **Verify the Pod:**

   After deploying the Pod, check its status to ensure it is running correctly. This step involves confirming that the Pod is listed and in the `Running` state.

### 3. **Create a Service to Expose Redis**

To make the Redis Pod accessible:

1. **Expose the Redis Pod:**

   Create a NodePort service to expose the Redis Pod. This service configuration allows external access to the Redis Pod by mapping a port on the Node to the Pod’s port.

2. **Verify the Service:**

   After creating the service, check its status to confirm that it has been set up correctly. This involves ensuring that the service is listed and that the correct NodePort is assigned.

3. **Get Service Details:**

   Retrieve detailed information about the service to obtain the assigned NodePort. This helps in accessing the Redis server from outside the Kubernetes cluster.

### 4. **Access Redis Using `redis-cli`**

To interact with the Redis server:

1. **Find the Node IP and Port:**

   Identify the Node IP and combine it with the NodePort from the service to form the access URL for Redis.

2. **Run `redis-cli`:**

   You can access the Redis server using `redis-cli`. Depending on your setup, you can use one of the following methods:

   - **Using a Temporary Pod:** Run a temporary Redis container with `redis-cli` within Kubernetes. To access Redis using this method, use the following command inside the container:

     ```sh
     redis-cli -h redis-pod -p 6379
     ```

   - **Using Local `redis-cli`:** If you have `redis-cli` installed locally, you can connect directly to Redis using the Node IP and NodePort. Use the following command:

     ```sh
     redis-cli -h <Node-IP> -p <NodePort>
     ```

     Replace `<Node-IP>` with the IP address of the Node and `<NodePort>` with the port assigned to the service.

### 5. **Delete the Pod and Service (Optional)**

If you need to clean up the resources:

- Delete both the Redis Pod and the associated service to remove the deployment from your Kubernetes cluster.

## Additional Information

- Ensure your Kubernetes cluster is properly set up and running before you begin the deployment.
- The Redis Pod is exposed using a NodePort, which allows it to be accessed from outside the cluster. By default, Redis uses port 6379.

## Troubleshooting

If you encounter issues:

- **Check Pod Logs:** View the logs of the Redis Pod for troubleshooting.
- **Describe the Pod:** Get detailed information about the Pod to diagnose any issues.
- **Describe the Service:** Obtain detailed information about the service for troubleshooting purposes.
- **Check NodePort and IP:** Verify the NodePort and Node IP to ensure they are correctly configured.

## Contributing

Contributions to this project are welcome. If you wish to contribute:

1. Fork the repository.
2. Create a feature branch for your changes.
3. Commit your changes to the branch.
4. Push the branch to your forked repository.
5. Create a pull request to merge your changes into the main repository.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

For any questions, please reach out via email at [subhi.juhaina98@gmail.com](mailto:subhi.juhaina98@gmail.com).
