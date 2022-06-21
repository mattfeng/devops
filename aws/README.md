# AWS

## EC2 instances

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

### Terminate instance

