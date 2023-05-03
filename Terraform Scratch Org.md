# Terraform help with Salesforce Scratch Org

As of my knowledge cut-off date in September 2021, there isn't a native Terraform provider for managing Salesforce scratch orgs directly. The Salesforce Terraform provider mentioned earlier is more focused on managing Salesforce metadata and configurations, not scratch orgs.

However, you can use a combination of Terraform and the Salesforce CLI (SFDX) to automate the creation and management of scratch orgs. You can use Terraform's `null_resource` and `local-exec` provisioner to execute SFDX commands.

Here's a basic example of how you might use Terraform and SFDX together to create and delete a scratch org:

1. First, ensure you have the Salesforce CLI (SFDX) installed on your system and authenticated with your Dev Hub.

2. Create a `scratch-org-config.json` file with the desired scratch org configuration:

```json
{
  "orgName": "My Company",
  "edition": "Developer",
  "features": ["API", "AuthorApex"]
}
```

3. Create a Terraform configuration file (`main.tf`) with a `null_resource` and the `local-exec` provisioner:

```hcl
resource "null_resource" "scratch_org" {
  triggers = {
    config = jsondecode(file("scratch-org-config.json"))
  }

  provisioner "local-exec" {
    command = "sfdx force:org:create -f scratch-org-config.json --setalias my_scratch_org --durationdays 7 --setdefaultusername --json"
  }

  provisioner "local-exec" {
    when    = destroy
    command = "sfdx force:org:delete -u my_scratch_org -p --json"
  }
}
```

In this example, the `null_resource` will execute the `sfdx force:org:create` command to create a scratch org using the `scratch-org-config.json` file. When the resource is destroyed (e.g., when you run `terraform destroy`), it will execute the `sfdx force:org:delete` command to delete the scratch org.

This is a basic example and may not cover all possible use cases for managing scratch orgs. You may need to customize the configuration and commands to fit your specific requirements. Note that this approach uses the Salesforce CLI and may be more of a workaround than a native Terraform solution.
