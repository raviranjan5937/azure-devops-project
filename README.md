# azure-devops-project



# Adjust the name of your organization and repository
git clone https://github.com/raviranjan5937/contoso.git contoso && cd contoso

Open vscode
Modify rover image: aztfmod/rover:1.4.6-2305.2907
git clone https://github.com/Azure/caf-terraform-landingzones.git landingzones
cd landingzones 
git checkout 2203.1
rover login
Modify /tf/caf/landingzones/templates/ansible/load_deployments_alz.yaml and add the content from https://github.com/raviranjan5937/azure-devops-project/blob/main/tf/caf/landingzones/templates/ansible/load_deployments_alz.yaml

Run: /tf/caf/landingzones/templates/platform/deploy_platform.sh
