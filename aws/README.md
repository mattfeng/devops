# AWS

## EC2 instances

### Get default VPC id
- `aws ec2 describe-vpcs --query "Vpcs[?IsDefault].[VpcId]"`

### Create security group
- `aws ec2 create-security-group`
- `aws ec2 describe-security-groups`

### Authorize SSH ingress in security group
- `aws ec2 authorize-security-group-ingress`

### Get VPC subnet
- `aws ec2 describe-subnets --filters "Name=vpc-id,Values=<vpc-id>"`

### Create key pair
- `aws ec2 create-key-pair --key-name <keyname> --query 'KeyMaterial' --output text > <keyname>.pem`

### List Ubuntu AMIs

- `aws ec2 describe-images --query "sort_by(Images, &CreationDate)[].[ImageId,CreationDate,Description]" --filters "Name=architecture,Values=x86_64" "Name=name,Values=*ubuntu-focal*" "Name=image-type,Values=machine" --output text`

```bash
aws ec2 describe-images \
  --query "sort_by(Images, &CreationDate)[].[ImageId,CreationDate,Description]" \
  --filters "Name=architecture,Values=x86_64" \
            "Name=name,Values=*ubuntu-focal*" \
            "Name=image-type,Values=machine"
  --output text
```

- Common AMIs
  - Ubuntu 20.04 LTS (Focal): `ami-0c24d345ea91339ee`

### List instances
- `aws ec2 describe-instances --filters "Name=instance-type,Values=t2.micro" --query "Reservations[].Instances[].InstanceId"`
- Filters
  - `Name=instance-type,Values=<instance type>`

### Launch instance
- `aws ec2 run-instances --image-id <ami-id> --count 1 --instance-type t2.medium --key-name <key name> --security-group-ids <sg id> --subnet-id <subnet id>`

### Stop instance

### Terminate instance

