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
New-SLTenant -Subscription '#' -FarmName '#' -MVersion '#'
exit
```

2. redisDB creation: Memory based


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
   New-SLTenant -Rerun -TenantName <tenant name previous command created>  -Subscription ‘STYLELABS SaaS PROD 01' -FarmName '#'

   eg: New-SLTenant -Rerun -TenantName mss-p-037 -Subscription 'STYLELABS SaaS PROD 01' -FarmName 'mss-f8'
   ```