<h1 style="color:green">Scale instances</h1>

#### Scale Up CPU on graph server
Graph server is running out of CPU. lets upscale it to the following:

```
Graph:
    resource_limits:
       cpu: 2
       cpu: 4
       memory: 8
    requests_percentage:
       memory: 50
       cpu: 50
```
1. Edit instance config file and add those lines
2. As we are upscaling graph, we are on the **processing-services** and the service to restart is **graph**
    ```
    ansible-playbook contenthub_deploy.yml -t restart-aks,processing-services -e service=graph
    ```
    **Note:** If it was **media cluster** that we had to upscale, we should have ran:
    ```
    ansible-playbook contenthub_deploy.yml -t restart-aks,processing-agent -e service=media
    ```
1. Get ARA logs
2. Run HealthCheck with:
    ```
    kubectl --context sl-aksd-weu-01 -n unlv-q-002 patch statefulset unlv-q-002-graph --patch '{"spec":{"template": {"spec":{"containers":[{"livenessProbe": {"periodSeconds": 60,"timeoutSeconds": 30},"name": "graph","readinessProbe": {"periodSeconds": 15,"timeoutSeconds": 5}}]}}}}'

    Output:
    statefulset.apps/unlv-q-002-graph patched
    ```
3. Put the result in the channel and on the ticket

#### Sample result:
```
Upscaled unlv-q-002 CPU to the following:

Graph:
    resource_limits:
       cpu: 2
       cpu: 4
       memory: 8
    requests_percentage:
       memory: 50
       cpu: 50

ansible-playbook contenthub_deploy.yml -t restart-aks,processing-services -e service=graph

Output:
slkubectl m get hpa

NAME                             REFERENCE                               TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
unlv-q-002-processingagent-hpa   Deployment/unlv-q-002-processingagent   4%/150%   8         16        8          57d
```