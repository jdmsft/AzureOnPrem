# AzureOnPrem

___Azure OnPremises Environment Simulation___

* OnPremises Virtual Network
* OnPremises Domain Controller with new Active Directory forest
* OnPremises domain-joined Hyper-V hypervisor (empty)

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjdmsft%2FAzureOnPrem%2Fmaster%2Fmain.json" target="_blank"><img src=".github/DeployToAzure.png" width="150" /></a>
<a href="https://github.com/jdmsft/AzureOnPrem" target="_blank"><img src=".github/OpenInGithub.png" width="150" /></a> 

_Deployment time : ~ 30 min_

# Configuration

* ADDS : Standard_D2sv3
* HV : Standard_D4sv3

# Process

1) Run main.json
2) main.json deploy resources based on /Templates nested files
3) nested template (DC VM) call /Automation/ADDS/NewForest/1_Script_PrepareDSC.ps1
4) main.json call /Automation/ADDS/NewForest/2_DSC_NewADForest.json wich deploy 2_DSC_NewADForest.ps1.zip as VM extension
5) nested template (HyperV VM) call /Automation/HyperV wich deploy install and confiuge HyperV as VM extension

# Sources 

Project inspired by these components projects : 

* __ADDS__ : https://github.com/Azure/azure-quickstart-templates/tree/master/301-create-ad-forest-with-subdomain

* __Hyper-V__ : https://github.com/deltadan/AzureNestedHyperV
