<h1 style="color:red">Maintenance</h1>

## Simple farm *non-rolling* maintenance:
- Inform client in slack that you do maintenance 
```
@here Hello, we are starting maintenance on google dev/qa 
```
- run : 
```
tmux new -s nr-main
slansible
vault_connect
farm=tccc-f6 ansible-playbook sl-farm_maintenance_app_offline.yml
```
- Keep ara logs for later

## Simple farm *rolling* maintenance:
- Inform client in slack that you do maintenance 
```
@here Hello, we are stating maintenance on google dev/qa 
```
- run : 
```
slansible
vault_connect
farm=pg-f13 ansible-playbook sl-farm_maintenance_rolling.yml
```
- Keep ara logs for later
