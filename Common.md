<h1 style="color:red">Common commands</h1>

## SSH:
- List ssh identities: ```ssh-add -l ```
- Add ssh identity: ```ssh-add ```

## Activate virtual env:
- ```source $HOME/slinfraVE/bin/activate```

## Tmux:
- Create Tmux session: ```tmux new -s test```
- Detach from session: ```CTRL + B then D```
- Attach session: ```tmux attach -t test```
- Close session: ```exit```

## connect to windows machine in farm (processing machine) :
```
slconnect goo-f4-procm02
```

## Connect to JumpBox:
```ssh loi@stylelabs.com@slstep001.stylelabs.cloud```



## Redeploy webapps, portals or processing
``` ansible-playbook contenthub_deploy.yml -t webapps ```
``` ansible-playbook contenthub_deploy.yml -t restart-portal -e app=portal ```
``` ansible-playbook contenthub_deploy.yml -t restart-portal -e app=processing ```

## Restart webapps, portals or processing
``` ansible-playbook contenthub_deploy.yml -t stop-services,start-services -l '*procd0*' ```

## Clear graph and remove graph and audit queues (case unlv-p-001)
- slcontext
- Get pods : ```slkubectl d get pods```
- Stop graph pod: ``` slkubectl d scale sts pg-q-016-graph --replicas=0 ```
- Go to client url with force passive true or take url from ops portal
``` ansible-playbook contenthub_deploy.yml -t stop-services,start-services -l '*procd0*' ```

## start graph only:
``` ansible-playbook contenthub_deploy.yml -t graph-rebuild ```

