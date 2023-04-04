# terraform-null-input-output

Pass in anything, get it back. Useful for testing Terragrunt builtin functions.

```
# terragrunt.hcl
terraform {
  source = "git@github.com:iangrunt/terraform-null-input-output.git?ref=main"
}

locals {
  project = read_terragrunt_config(find_in_parent_folders("project.hcl"))
}

inputs = {
  input = {
    project_id  = local.project.locals.project_id
    namespace   = "iangrunt"
    environment = "prod"
  }
}

```

```
$ terragrunt plan

Changes to Outputs:
  + output = {
      + environment = "prod"
      + namespace   = "iangrunt"
      + project_id  = "project-delta"
    }
```

<!-- BEGIN_TF_DOCS -->

<!-- END_TF_DOCS -->
