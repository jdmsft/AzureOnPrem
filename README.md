# NOTES


<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjdmsft%2FAzureOnPrem%2Fmaster%2Fmain.json" target="_blank">![Button to deploy project to Azure.](.github/deploy-to-azure.png "Deploy the project to Azure")</a>

AD Forest deployment time : ~ 24 min

ADDS : Standard_D2sv3
HV : Standard_D4sv3

# Notes

1) Run main.json
2) main.json deploy resources based on /Templates nested files
3) nested template (DC VM) call /Automation/ADDS/NewForest/1_Script_PrepareDSC.ps1
4) main.json call /Automation/ADDS/NewForest/2_DSC_NewADForest.json wich deploy 2_DSC_NewADForest.ps1.zip as VM extension

# Sources 

Project inspired to these projects : 

* AD Forest : https://github.com/Azure/azure-quickstart-templates/tree/master/301-create-ad-forest-with-subdomain

* Hyper-V : https://github.com/deltadan/AzureNestedHyperV
