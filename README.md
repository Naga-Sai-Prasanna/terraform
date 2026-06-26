# Terraform Practice

A collection of Terraform configurations covering core concepts, written as hands-on practice while learning Terraform — from basic resource creation through variables, functions, loops, data sources, provisioners, remote state, and multi-environment workspaces.

## What This Covers

Each folder is a self-contained Terraform configuration focused on one specific concept, mostly using AWS as the provider and EC2 instances as the example resource.

## Folders

| Folder | Topic |
|--------|-------|
| `conditions/` | Conditional expressions in Terraform |
| `count/` | The `count` meta-argument for creating multiple resources |
| `data_sources/` | Using `data` blocks to fetch existing infrastructure info |
| `dynamic/` | `dynamic` blocks for generating repeated nested blocks |
| `ec2/` | Basic EC2 instance creation |
| `for_each/` | The `for_each` meta-argument for creating multiple resources from a map/set |
| `functions/` | Built-in Terraform functions (including `lookup`) |
| `import/` | Importing existing infrastructure into Terraform state |
| `locals/` | Local values (`locals`) for reusable expressions |
| `provisioners/` | Provisioners for running scripts/commands on resource creation |
| `remote-state/` | Configuring and using remote state |
| `terraform-multienv/` | Multi-environment setup using `tfvars` per environment and Terraform workspaces |
| `variables/` | Input variables and `.tfvars` files |

### `terraform-multienv/` in detail

- `tfvars/` — separate `dev/` and `prod/` folders, each with its own `backend.tf` and `terraform.tfvars`, demonstrating environment-specific configuration via variable files
- `workspace/` — the same environment-separation goal achieved using Terraform workspaces instead of separate `tfvars` folders

## Prerequisites

- Terraform installed locally
- AWS CLI configured with credentials that have permission to create the relevant resources (mainly EC2 instances)

## Usage

From inside any topic folder:

```bash
cd ec2
terraform init
terraform plan
terraform apply
```

Tear down resources when done to avoid ongoing AWS charges:

```bash
terraform destroy
```

For the multi-environment example:

```bash
cd terraform-multienv/tfvars
terraform init
terraform apply -var-file="dev/terraform.tfvars"
```

## Notes

- `.terraform/` cache directories, `.tfstate` files, and provider binaries are intentionally excluded from version control (see `.gitignore`) — they're local artifacts, not source code, and shouldn't be committed.
- Each folder is independent; running `terraform init` in one does not affect the others.

## Status

This is a personal learning/practice repo for Terraform fundamentals, part of a broader DevOps practice set also covering Ansible, Shell scripting, Docker, and EKS in separate repos.
