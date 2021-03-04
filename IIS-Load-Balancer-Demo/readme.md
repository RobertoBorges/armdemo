# Create a simple loadbalanced iis environment with 2 vms

Simple ARM file to demo how to deploy a full configuration of Loadbalancer with rules and back-end pool

```powershell
$password="P@ssword1" | ConvertTo-SecureString -AsPlainText -Force

az group create --name mydemodeployement --location canadaeast

az deployment group create `
--name demodeployment  `
--resource-group mydemodeployement `
--template-file demo.json `
--parameters virtualMachine_vm1_name=vm001 virtualMachine_vm2_name=vm002 loadBalancers_lbldemo_name=lbldemo `
networkInterfaces_vm1160_name=vm1160 networkInterfaces_vm2781_name=vm2781 `
publicIPAddresses_loadbalancer_name=lblipname networkSecurityGroup_name=nsgdemo01 virtualNetworks_name=demovnet `
bastionHosts_name=bastiondemo publicIPAddresses_bastion_name=ipbastiondemo adminpassword=$password
```
