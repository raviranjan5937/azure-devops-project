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

### Regenerate the definition folder

For your reference, if you need to re-generate the YAML definition files later, you can run the following command: 

```bash
ansible-playbook /tf/caf/landingzones/templates/ansible/walk-through-single.yaml \
  --extra-vars "@/tf/caf/platform/definition/ignite.yaml"

```%       
