<h1 style="color:green">Graph related tasks</h1>

##### Stop graph pod and remove it (case unlv-p-001)
<h6 style="color:red">Get confirmation to start working</h6>

- slcontext
- Get pods : ```slkubectl d get pods```
- Stop graph pod: ``` slkubectl d scale sts pg-q-016-graph --replicas=0 ```
- Keep ara logs link

### Clean/Clear graph queue both: IN / WIP
<h6 style="color:red">Get confirmation to start working</h6>

- slcontext
- Create a tmux session: ```tmux new -s graph-all```
    ```ansible-playbook m_commandline.yml -e 'command=clean-queue cmdargs=["-queue=graph","-allStates"]' ```
- Keep ara logs link

### Clean/Clear audit queue: WIP
<h6 style="color:red">Get confirmation to start working</h6>

- slcontext
- Create a tmux session: ```tmux new -s graph-wip```
- Run:
    ```ansible-playbook m_commandline.yml -e 'command=clean-queue cmdargs=["-queue=audit","-states=wip"]' ```
- Keep ara logs link


### Remove a queue: Graph
<h6 style="color:red">Get confirmation to start working</h6>

- slcontext
- Create a tmux session: ```tmux new -s graph-rm```
- Run:
    ``` ansible-playbook m_commandline.yml -e 'command=remove-queue cmdargs=["-queue=graph"]' ```
- Keep ara logs link


### Run graph only:
<h6 style="color:red">Get confirmation to start working</h6>

- slcontext
- Create a tmux session: ```tmux new -s graph-in```
    ``` ansible-playbook contenthub_deploy.yml -t graph-rebuild ```
- Keep ara logs link

