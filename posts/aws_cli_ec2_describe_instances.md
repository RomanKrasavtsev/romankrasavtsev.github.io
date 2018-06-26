```
aws ec2 describe-instances --instance-ids ID \
--query 'Reservations[*].Instances[*].{
Name: Tags[?Key==`Name`] | [0].Value,
InstanceType: InstanceType,
KeyName: KeyName,
LaunchTime: LaunchTime,
AvailabilityZone: Placement.AvailabilityZone,
PublicDnsName: PublicDnsName,
PublicIpAddress: PublicIpAddress,
PrivateDnsName: PrivateDnsName,
PrivateIpAddress: PrivateIpAddress,
VpcId: VpcId,
SubnetId: SubnetId
}' \
--output table
```
