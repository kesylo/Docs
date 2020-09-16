<h1 style="color:red">M Basics commands</h1>

## Restart Webapps
```
ansible-playbook contenthub.yml -t restart-webapps
```

## Redeploy Webapps
```
ansible-playbook contenthub_deploy.yml -t webapps
```

## Refresh rendition *Web_optimized*
```
ansible-playbook m_commandline.yml -e 'command=refresh-renditions cmdargs=["-all", "-renditions=web_optimized"]'
```

