**Part 1:**

**Backend Deployment Prerequisites:**

-> Ensure you have a Kubernetes cluster running.

-> kubectl should be configured to interact with your cluster.

-> Namespace project-plato should be created.

**Below manifest files are created for the backend deployment:**

backend-deployment.yaml

namespace.yaml

db1-configmap.yaml

db1-deployment.yaml

db1-service.yaml

db2-configmap.yaml

db2-deployment.yaml

db2-service.yaml

db2-secret.yaml

db2-configmap.yaml

network-policy.yaml

**Verification steps:**

• Deploy the Resources:** Apply all the manifests to the cluster. First create the namespace and then apply other files.

         kubectl apply –f  < filename.yaml >
         
• Verify Deployments and Services:

          kubectl get pods -n project-plato
          kubectl get services -n project-plato
          
Ensure that: The backend Pod is running. The db1 and db2 Pods are accessible on the correct ports.

• Validate Readiness and Liveness Probes: 
Confirm that the LivenessProbe is working by checking the events for true execution, and that the ReadinessProbe successfully verifies the connection to db1 on port 6379.

          kubectl describe pod < backendpodname > -n project-plato
   
• Test NetworkPolicy

          kubectl exec -it < backendpodname > -n project-plato -- nc -zv db1-service 6379

          kubectl exec -it < backendpodname > -n project-plato -- nc -zv db2-service 5432
   
• Validate Secrets for db2

          kubectl exec -it < db2-pod-name > -n project-plato -- printenv | grep DB2
