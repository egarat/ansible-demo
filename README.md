# ansible-demo
Ansible playbooks to demonstrate at the team meeting. These playbooks are modified samples provided by Microsoft and Hortonworks to create SQL Server instances and HDP clusters on Azure.

## Requirements

- Ansible 2.5+
- Python >=2.7 or >=3.4
- [Azure Service Principal](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal) or [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
- Pip to install azure[ansible]

## Preparations

### Azure Service Principal
If taking this approach, create or use an existing Azure Service Principal and configure your environment using the credentials. More information can be found [here](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/ansible-install-configure#create-azure-credentials).

### Azure CLI
In case Azure CLI has been installed, login in your shell using the `az login` command.

## Usage

Providing SQL instance on Azure

```bash
ansible-playbook azure-sql/sql_create.yml
```

Providing HDP instance

- Modify inventory in `static-hdp/inventory/static`
- Adjust variables in `static-hdp/playbooks/group_vars`
- Run the playbook

```bash
cd static-hdp
ansible-playbook playbooks/install_cluster.yml -i inventory/static -u <admin_user> -k -K
```


## Resources
- [ansible-hortonworks](https://github.com/hortonworks/ansible-hortonworks)
- [ansible-playbooks](https://github.com/Azure-Samples/ansible-playbooks)
