## Prerequisites
- kubectl


## Setup

- deploy the pods using the deployment
    ```bash
    kubectl apply -f deployment.yml
    ```

- check the status of the pods
    ```bash
    kubectl get pods --watch
    # or
    kubectl get pods -o wide
    ```

- deploy the service
    ```bash
    kubectl apply -f service.yml
    ```

- deploy the ingress
    ```bash
    kubectl apply -f ingress.yml
    ```

## [Local Deployment](https://kubernetes.github.io/ingress-nginx/deploy/#docker-desktop)

- create ingress controller
- enable port-forwarding

## Dashboard
To monitor the cluster from a browser UI, check out how to create a [Kubernetes Dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)
- create admin user
  ```
  kubectl apply -f dashboard/adminuser.yaml
  ```

- if you want to access the dashboard across all namespaces, you need to create a cluster role binding
  ```
  kubectl apply -f dashboard/role-binding.yaml
  ```

- create the access token
  ```
  kubectl -n kubernetes-dashboard create token admin-user
  ```

- start the proxy
  ```
  kubectl proxy
  ```

- use the generated token to access the [dashboard](http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/)
- once your're done, delete the admin user
  ```
  kubectl -n kubernetes-dashboard delete serviceaccount admin-user
  ```