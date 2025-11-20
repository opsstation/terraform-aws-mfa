# # 🏗️ Terraform-AWS-lb

[![OpsStation](https://img.shields.io/badge/Made%20by-OpsStation-blue?style=flat-square&logo=terraform)](https://www.opsstation.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Terraform](https://img.shields.io/badge/Terraform-1.13%2B-purple.svg?logo=terraform)](#)
[![CI](https://github.com/OpsStation/terraform-aws-ec2/actions/workflows/ci.yml/badge.svg)](https://github.com/OpsStation/terraform-aws-ec2/actions/workflows/ci.yml)

> 🌩️ **A production-grade, reusable AWS Ec2 module by [OpsStation](https://www.opsstation.com)**
> Designed for reliability, performance, and security — following AWS networking best practices.
---

## 🏢 About OpsStation

**OpsStation** delivers **Cloud & DevOps excellence** for modern teams:
- 🚀 **Infrastructure Automation** with Terraform, Ansible & Kubernetes
- 💰 **Cost Optimization** via scaling & right-sizing
- 🛡️ **Security & Compliance** baked into CI/CD pipelines
- ⚙️ **Fully Managed Operations** across AWS, Azure, and GCP

> 💡 Need enterprise-grade DevOps automation?
> 👉 Visit [**www.opsstation.com**](https://www.opsstation.com) or email **hello@opsstation.com**

---
## 🌟 Features

- ✅ Enables and manages **AWS Multi-Factor Authentication (MFA)** for IAM users
- ✅ Supports both **virtual MFA devices** (Google Authenticator, Authy) and **hardware MFA tokens**
- ✅ Automatically configures **MFA-enabled IAM policies** for secure access control
- ✅ Supports **console login**, **CLI**, and **API-level** MFA authentication mechanisms
- ✅ Integrates seamlessly with **IAM Users**, **IAM Groups**, and **IAM Roles**
- ✅ Optional enforcement of **root account MFA** for maximum security
- ✅ Supports **MFA-protected API operations** to prevent unauthorized sensitive actions
- ✅ Enables tagging and naming conventions through the **Labels module**
- ✅ Follows AWS best practices for **identity security**, **compliance**, and **least privilege**
- ✅ Fully compatible with other **OpsStation Terraform IAM modules**
---

# Example : mfa
```hcl
module "mfa" {
  source      = "git::https://github.com/opsstation/terraform-aws-mfa.git?ref=v1.0.0"
  name        = "mfa1"
  environment = "test"
  users       = []
  groups      = []

}

```
### 🔐 Outputs (AWS MFA Module)

| Name                      | Description                                                                           |
|---------------------------|----------------------------------------------------------------------------------------|
| `user_name`               | The **IAM user name** for whom MFA has been enabled.                                  |
| `mfa_enabled`             | Shows whether **MFA is enabled** (`true/false`) for the user.                         |
| `mfa_device_serial`       | The **serial number** of the assigned MFA device (virtual or hardware).               |
| `mfa_device_type`         | The type of the MFA device (**virtual** or **hardware token**).                       |
| `mfa_status`              | The current **status of MFA configuration** for the IAM user.                         |
| `policy_arn`              | The ARN of the **MFA-enforced IAM policy** attached to the user.                      |
| `attached_policies`       | A list of all **IAM policy ARNs** attached to the user for MFA enforcement.           |
| `user_arn`                | The **ARN of the IAM user** with MFA enabled.                                         |
| `login_profile_status`    | Indicates whether the **login profile** exists (`true/false`) for console access.     |
| `access_key_status`       | Indicates whether the user’s **access keys** are active and MFA-protected.            |
| `tags`                    | A mapping of **tags** assigned to the IAM user and MFA resources.                     |


### ☁️ Tag Normalization Rules (AWS)

| Cloud | Case      | Allowed Characters | Example                            |
|--------|-----------|------------------|------------------------------------|
| **AWS** | TitleCase | Any              | `Name`, `Environment`, `CostCenter` |

---
