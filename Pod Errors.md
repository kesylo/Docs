## Issues with pods

If Renditions don't work or jobs are stucked in the queue
- get pods list and Find the pod with issue
    ```
    slkubectl d get pods
    slkubectl m get pods
    ```
- look at last 10 log entries (-c for pods with multiple containers)
    ```
    slkubectl d logs --tail 10 vod-p-001-graph-0 -c graph
    ```
- reboot it 
    ```
    slkubectl d delete pod <podname1> <podname2>
    ```

- get list of running pods
    ```
    slkubectl d get sts
    ```
  - If we have a pod with READY 0/0
  - Scale up with 
  ```
  slkubectl d scale sts vod-p-001-core --replicas=1
  ```