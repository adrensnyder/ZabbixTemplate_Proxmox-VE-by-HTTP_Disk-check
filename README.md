# Proxmox VE by HTTP - Disk check
Zabbix Template that enable monitoring of Ceph and Smart on Proxmox PVE nodes  

It used to be added to the official [Proxmox VE by HTTP](https://www.zabbix.com/integrations/proxmox) template because it shares many MACROS  
Tested with Proxmox VE by HTTP on Zabbix Server 6.0 LTS  

All the MACROS used are explained in the template  

## Instructions
Add SNMP interface with the ip of the Proxmox node  

Edit macro {$PVE.HOSTNAME} with the hostname of the node  

Create group "zabbix" in Permissions - Groups  
Create user "zabbix" with group "Zabbix" in Permissions - Users  

Create an API token for user "zabbix@xxx" with token id "zabbix"  
Please copy the TokenID and Secret separately as they will not be displayed afterwards  

Create a new role in Roles named "Zabbix" with:  
Datastore.Audit  
Pool.Audit  
SDN.Audit  
Sys.Audit  
VM.Audit  

Add User/Group/Api permission in Permissions with:  
Path: /  
User: [The zabbix User/Group/Api]  
Role: Zabbix  

Note: All the 3 permissions are needed to get the template working  

In the Zabbix Host modify the Macro {$PVE.TOKEN.ID} and {$PVE.TOKEN.SECRET} with the values we saved before  

There credentials are shared across all the nodes. Need to be created only one time for all of them  
