# Developer notes

## RegionMap

To update the region map execute the following lines in your terminal:

```
$ regions=$(aws ec2 describe-regions --query "Regions[].RegionName" --output text)
$ for region in $regions; do ami=$(aws --region $region ec2 describe-images --filters "Name=name,Values=amzn-ami-hvm-2015.09.1.x86_64-gp2" --query "Images[0].ImageId" --output "text"); echo "\"$region\": {\"AMI\": \"$ami\"},"; done
```
