# Cloud Adoption Framework landing zones for Terraform - Ignite the Azure Platform and landing zones


:rocket: START HERE: [Follow the onboarding guide from](https://aztfmod.github.io/documentation/docs/enterprise-scale/landingzones/platform/org-setup)


For further executions or command, you can refer to the following sections

## Commands

### Rover ignite the platform

Rover ignite will  process the YAML files and start building the configuration structure of the TFVARS. 

Please note that during the creation of the platform landingones you will have to run rover ignite multiple times as some deployments are required to be completed before you can perform the next steps. 

The best course of actions is to follow the readme files generated within each landing zones, as rover ignite creates the tfvars and also the documentation.

Once you are ready to ingite, just run:

```bash
rover login -t ranjanravi5937outlook.onmicrosoft.com -s a8c08892-07e1-44cb-b7ec-c71cd3e04452

ansible-playbook /tf/caf/landingzones/templates/ansible/ansible.yaml \
  --extra-vars "@/tf/caf/platform/definition/ignite.yaml"

```

### Next step

Once the rover ignite command has been executed, go to your configuration folder when the platform launchpad configuration has been created.

Get started with the [launchpad](/tf/caf/platform/definition/level0/launchpad)



## References

Whenever needed, or under a profesional supervision you can use the following commands

### Clone the landingzone project (Terraform base code)

```bash
git clone https://github.com/Azure/caf-terraform-landingzones.git /tf/caf/landingzones
cd /tf/caf/landingzones && git pull
git checkout 2203.0

```



### Launchpad

```bash
# Login to the subscription Free Trial with the user ranjan.ravi5937_outlook.com#EXT#@ranjanravi5937outlook.onmicrosoft.com
rover login -t ranjanravi5937outlook.onmicrosoft.com -s a8c08892-07e1-44cb-b7ec-c71cd3e04452

cd /tf/caf/landingzones
git fetch origin
git checkout 2203.0
git pull

rover \
  -lz /tf/caf/landingzones/caf_launchpad \
  -var-folder /tf/caf/configuration/level0/launchpad \
  -tfstate_subscription_id a8c08892-07e1-44cb-b7ec-c71cd3e04452 \
  -target_subscription a8c08892-07e1-44cb-b7ec-c71cd3e04452 \
  -tfstate caf_launchpad.tfstate \
  -launchpad \
  -env contoso \
  -level level0 \
  -p ${TF_DATA_DIR}/caf_launchpad.tfstate.tfplan \
  -a plan

```

If the plan is not successfull you need to come back to the yaml ignite.yaml, fix the values, re-execute the rover ignite and then rover plan.


```bash 
# On success plan, execute

rover \
  -lz /tf/caf/landingzones/caf_launchpad \
  -var-folder /tf/caf/configuration/level0/launchpad \
  -tfstate_subscription_id a8c08892-07e1-44cb-b7ec-c71cd3e04452 \
  -target_subscription a8c08892-07e1-44cb-b7ec-c71cd3e04452 \
  -tfstate caf_launchpad.tfstate \
  -launchpad \
  -env contoso \
  -level level0 \
  -p ${TF_DATA_DIR}/caf_launchpad.tfstate.tfplan \
  -a apply

```

Execute a rover logout and rover login in order to make sure your azure sessions has the Azure groups membership updated.

```bash
rover logout

rover login -t ranjanravi5937outlook.onmicrosoft.com

# On success, re-execute the rover ignite

ansible-playbook /tf/caf/landingzones/templates/ansible/ansible.yaml \
  --extra-vars "@/tf/caf/platform/definition/ignite.yaml"

```

# Next steps

When you have successfully deployed the launchpad you can  move to the next step.

 [Deploy the credentials landing zone](../credentials/readme.md)


# To destroy the launchpad

Destroying the launchpad is a specific opertion that requires the tfstate to be first downloaded in the rover and then run the terraform destroy command. Note the action to use is -a destroy

```bash

rover \
  -lz /tf/caf/landingzones/caf_launchpad \
  -var-folder /tf/caf/configuration/level0/launchpad \
  -tfstate_subscription_id a8c08892-07e1-44cb-b7ec-c71cd3e04452 \
  -target_subscription a8c08892-07e1-44cb-b7ec-c71cd3e04452 \
  -tfstate caf_launchpad.tfstate \
  -launchpad \
  -env contoso \
  -level level0 \
  -a destroy

```

### Regenerate the definition folder

For your reference, if you need to re-generate the YAML definition files later, you can run the following command: 

```bash
ansible-playbook /tf/caf/landingzones/templates/ansible/walk-through-single.yaml \
  --extra-vars "@/tf/caf/platform/definition/ignite.yaml"

```%       
