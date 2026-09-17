# HCL syntax rules and Terraform single-file usage
in Terraform, a single .tf file can contain the full configuration, and that is perfectly valid.

General HCL syntax rules
HCL is a declarative configuration language.
Files use blocks and arguments:

```markdown
block_type "label" { ... }
argument = value
```
Each block has a specific shape depending on the resource or provider.
Strings are quoted: "us-east-1"
Numbers and booleans are unquoted: 1, true
Comments use:
# ...
// ...
In Terraform specifically
You can place:

```
terraform {} block
provider {} block
resource {} blocks
variable {} blocks
output {} blocks
module {} blocks
```
all in one file, or spread across many .tf files.

Practical rule
Terraform merges all .tf files in the same directory into one configuration set. So:

One file is valid
Many files are also valid
The main thing is that the syntax must be correct and blocks must match Terraform schema

wrong: resource ec2_instance "example"
correct: resource "aws_instance" "example"

HCL syntax is block-based, with quoted labels and assignment-style arguments.
The general rule is: each Terraform object must use the correct block type and valid argument names.

whitespace is mostly ignored
punctuation and block structure matter more than exact spacing



terraform init
terraform plan
terraform apply

