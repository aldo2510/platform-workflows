# Platform Workflows

Reusable GitHub Actions and governance workflows for Terraform repositories.

## Pipeline

```
fmt -> init -> validate -> lint -> security -> plan
```

The workflows are intended to run on pull requests and prevent unsafe Terraform changes from reaching the default branch.

## Planned checks

- Terraform format and validation
- TFLint
- Checkov
- Trivy IaC scanning
- Terraform plan
- Optional policy checks
