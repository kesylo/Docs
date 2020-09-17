<h1 style="color:green">Tenant creation (ProSaaS)</h1>

#### Prerequisites (Gte from Kwintten):

- **Location** : East US (In the ticket)
- **License details** : DAM, PCM and CMP (In the ticket)
- **farm-name** :  Based on the region (See below)
- **m_version** : 3.4.1 (current stable release)
- **subscription name** : STYLELABS SaaS Prod 01 (For all proSaaS)
- **RedisDB** : Memory Based (For all proSaaS)
- **Vault in 1password** : 

1. Create tenant : <span style="color:red">Verify well</span>
```
slansible
vault_connect
pwsh
Import-Module SLAzure
New-SLTenant -Subscription 'STYLELABS SaaS Prod 01' -FarmName '#' -MVersion '#'
exit
```

2. redisDB creation: Memory based

video

3. ECE Cluster
   
ok
farm=ece-01-aue tenant=mss-p-038 ansible-playbook sl-ece-cluster-create.yml  -e cluster_type=shared -e shared_cluster_name=mss-p-shared-002 -e m_version=3.4



Set-SLTenantConfig -Subscription 'STYLELABS SaaS PROD 01' -TenantName 'mss-p-013' -RedisUrl 'redis-18796.internal.c131.west-eu.azure.cloud.redislabs.com:18796' -RedisPass 'xxxxxxxxxxxxxx'
	NOTE: redisurl should be Private Endpoint of the corresponding redislabs db.
1. ECE

Check available memory on ECE cluster - Manual

url: https://ece-01-<location>.stylelabs.io:12443/ 

      example: https://ece-01-weu.stylelabs.io:12443/
Check the correct cluster region (weu or eus or aue or wus2) - Manual
Naming-convention: <customer name>-<subscription purpose: q/d/p>-shared-001, Example:  mss-p-shared-001 for ProSAAS customer. For enterprise it will be according to tenant name.  Please refer to other tenant names from ece url

ECE setup  - SLAnsible ( Run from Jumpbox )

 farm=ece-01-weu tenant=mss-p-013 ansible-playbook sl-ece-cluster-create.yml 
 <https://mansible-ara.stylelabsdemo.com/reports/b82ec046-25c5-4666-a4e1-057ccae77178.html>





ADD CONFIG FILE: VIDEO


DEPLOY:
mansible
slcontext tenant
ansible-playbook contenthub_deploy.yml
GET LOGS




#### More
1. Get Farm-name:
   - Azure portal -> Subscriptions -> Select **STYLELABS SaaS Prod 01**
   - then **Ressource groups** -> filter on your location 
   - Just get the farm name (It's the one with ...-f. eg: MSS-F8)

2. Get subscription from Farm-name:
   - Azure portal -> VM -> Select **all subscriptions** in dropdown list
   - Type **farm-name** and you can see the subscription

3. If error during step 1, use this command:
   ```
   New-SLTenant -Rerun -TenantName 'tenant name previous command created'  -Subscription ‘STYLELABS SaaS PROD 01' -FarmName '#'

   eg: New-SLTenant -Rerun -TenantName 'mss-p-037' -Subscription 'STYLELABS SaaS PROD 01' -FarmName 'mss-f8'
   ```