<h1 style="color:green">Graph related tasks</h1>

##### Stop graph pod and remove it (case unlv-p-001)
<h6 style="color:red">Get confirmation to start working</h6>

- slcontext
- Get pods : ```slkubectl d get pods```
- Stop graph pod: ``` slkubectl d scale sts pg-q-016-graph --replicas=0 ```
- Keep ara logs link


### Clean/Clear queue:
<h6 style="color:red">Get confirmation to start working</h6>

- Case: **Flow-all** state: **IN**
    ```
    tmux new -s clear-queue
    mansible
    vault_connect
    slcontext -t unlv-p-001
    ansible-playbook m_commandline.yml -e 'command=clean-queue cmdargs=["-queue=flow-all","-states=in"]'
    # For all states 
    ansible-playbook m_commandline.yml -e 'command=clean-queue cmdargs=["-queue=flow-all","-allStates"]'
    ```
- Get ARA logs


### Remove a queue:
<h6 style="color:red">Get confirmation to start working</h6>

- Case: **Graph**
    ```
    tmux new -s rm-queue
    mansible
    vault_connect
    slcontext -t unlv-p-001
    ansible-playbook m_commandline.yml -e 'command=remove-queue cmdargs=["-queue=audit"]'
    ```
- Get ARA logs


### Graph rebuild:
<h6 style="color:red">Get confirmation to start working</h6>

```
tmux new -s graph-rebuild
mansible
vault_connect
slcontext -t unlv-p-001
ansible-playbook contenthub_deploy.yml -t graph-rebuild
```
- Get ARA logs