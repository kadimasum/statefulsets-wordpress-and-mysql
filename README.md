
# WordPress and MySQL on Kubernetes

This project demonstrates the deployment of WordPress and MySQL on Kubernetes using StatefulSets. WordPress relies on MySQL as its backend, and the stateful nature of StatefulSets ensures stable storage and network identities for these applications.

# Table of Contents
  - [Prerequisites](#prerequisites)
  - [Project Structure](#project-structure)
  - [Deployment Steps](#deployment-steps)
  - [Customization](#customization)
  - [Cleanup](#cleanup)
  - [License](#license)
  - [Conclusion](#conclusion)

## Prerequisites

- A running Kubernetes cluster
- `kubectl` command-line tool configured to communicate with the cluster
- Basic understanding of Kubernetes concepts

## Project Structure

- **mysql-pv-pvc.yaml**: Defines PersistentVolume (PV) and PersistentVolumeClaim (PVC) for MySQL.
- **mysql-statefulset.yaml**: Deploys MySQL as a StatefulSet.
- **mysql-service.yaml**: Creates a Headless Service for MySQL.
- **wordpress-pv-pvc.yaml**: Defines PV and PVC for WordPress.
- **wordpress-statefulset.yaml**: Deploys WordPress as a StatefulSet.
- **wordpress-service.yaml**: Creates a Headless Service for WordPress.
- **LICENSE**: MIT License file.

## Deployment Steps

1. **Create MySQL PersistentVolume and PersistentVolumeClaim:**

    ```bash
    kubectl apply -f mysql-pv-pvc.yaml
    ```

2. **Create MySQL StatefulSet:**

    ```bash
    kubectl apply -f mysql-statefulset.yaml
    ```

3. **Create MySQL Headless Service:**

    ```bash
    kubectl apply -f mysql-service.yaml
    ```

4. **Create WordPress PersistentVolume and PersistentVolumeClaim:**

    ```bash
    kubectl apply -f wordpress-pv-pvc.yaml
    ```

5. **Create WordPress StatefulSet:**

    ```bash
    kubectl apply -f wordpress-statefulset.yaml
    ```

6. **Create WordPress Headless Service:**

    ```bash
    kubectl apply -f wordpress-service.yaml
    ```

7. **Access WordPress:**

    Obtain the NodePort or LoadBalancer IP:

    ```bash
    kubectl get svc wordpress
    ```

    Visit the obtained IP in your browser to access the WordPress installation page.

## Customization

- Adjust resource requests and limits in StatefulSet configurations based on your environment.
- Customize MySQL and WordPress environment variables in respective StatefulSet configurations.
- Modify storage configurations in PV/PVC files to use cloud-based storage solutions or other storage classes.

## Cleanup

To delete the deployed resources, run the following commands:

```
kubectl delete -f wordpress-service.yaml
kubectl delete -f wordpress-statefulset.yaml
kubectl delete -f wordpress-pv-pvc.yaml
kubectl delete -f mysql-service.yaml
kubectl delete -f mysql-statefulset.yaml
kubectl delete -f mysql-pv-pvc.yaml
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Conclusion

This project provides a robust example of deploying stateful applications on Kubernetes. Feel free to extend and modify it to suit your specific requirements and production environment.
