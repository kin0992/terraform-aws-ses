# terraform-aws-ses
Terraform module to create AWS SES

## Example usage

```hcl
module "ses" {
  source = "git::https://github.com/pagopa/terraform-aws-ses.git?ref=v1.0.0"
  domain = "pagopa.gov.it"

  iam_permissions = [
    "ses:SendCustomVerificationEmail",
    "ses:SendEmail",
    "ses:SendRawEmail",
    "ses:SendTemplatedEmail",
  ]

  ses_group_name = "PagoPaSES"
  user_name      = "ProjectPagoPa"

}
```

<!-- BEGIN_TF_DOCS -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.1.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 4.0.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 4.0.0 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_iam_access_key.ses_user](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_access_key) | resource |
| [aws_iam_group.ses_users](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_group) | resource |
| [aws_iam_group_policy.ses_group_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_group_policy) | resource |
| [aws_iam_user.ses_user](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_user) | resource |
| [aws_route53_record.cname](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_route53_record.txt](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/route53_record) | resource |
| [aws_ses_domain_dkim.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_domain_dkim) | resource |
| [aws_ses_domain_identity.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ses_domain_identity) | resource |
| [aws_iam_policy_document.ses_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_domain"></a> [domain](#input\_domain) | The domain name to assign to SES | `string` | n/a | yes |
| <a name="input_iam_allowed_resources"></a> [iam\_allowed\_resources](#input\_iam\_allowed\_resources) | Specifies resource ARNs that are enabled to send email. Wildcards are acceptable. | `list(string)` | `[]` | no |
| <a name="input_iam_permissions"></a> [iam\_permissions](#input\_iam\_permissions) | Permission for the Iam user. | `list(string)` | <pre>[<br>  "ses:SendRawEmail"<br>]</pre> | no |
| <a name="input_ses_group_name"></a> [ses\_group\_name](#input\_ses\_group\_name) | The name of the IAM group to create. | `string` | n/a | yes |
| <a name="input_ses_group_path"></a> [ses\_group\_path](#input\_ses\_group\_path) | The IAM Path of the group to create | `string` | `"/"` | no |
| <a name="input_user_name"></a> [user\_name](#input\_user\_name) | SES Iam user name. If null no user and group will be created. | `string` | n/a | yes |
| <a name="input_user_path"></a> [user\_path](#input\_user\_path) | Path in which to create the user. | `string` | `"/"` | no |
| <a name="input_verify_dkim"></a> [verify\_dkim](#input\_verify\_dkim) | Verify dkim | `bool` | `true` | no |
| <a name="input_verify_domain"></a> [verify\_domain](#input\_verify\_domain) | Verify domain? | `bool` | `true` | no |
| <a name="input_zone_id"></a> [zone\_id](#input\_zone\_id) | R53 zone id. | `string` | `null` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_dkim_tokens"></a> [dkim\_tokens](#output\_dkim\_tokens) | CNAME, dkim tokens. |
| <a name="output_ses_user_access_key_id"></a> [ses\_user\_access\_key\_id](#output\_ses\_user\_access\_key\_id) | n/a |
| <a name="output_ses_user_secret_access_key"></a> [ses\_user\_secret\_access\_key](#output\_ses\_user\_secret\_access\_key) | n/a |
| <a name="output_verification_token"></a> [verification\_token](#output\_verification\_token) | Verification token. TXT record. |
<!-- END_TF_DOCS -->