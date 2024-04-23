# aws-site-to-site-vpn-test-env
Intended to demonstrate or gain hands-on experience with AWS site-to-site VPN capabilities

This template is based on the blog here - https://aws.amazon.com/blogs/networking-and-content-delivery/simulating-site-to-site-vpn-customer-gateways-strongswan/

You will need to follow the instructions in the blog to establish prerequisites, and then use the template provided in this repo to deploy an IMDSv2 compliant strongSwan EC2 instance (vpn client.)

## Change Log
- Included `pInstanceVolumeType` parameter as deployment to AWS Local Zones may require the use of GP2 volumes
- Require `HttpTokens` and `HttpEndpoint` in `MetadataOptions` (Launch template properties)
- Include `BlockDeviceMappings` config for `rLaunchTemplate` that references `pInstanceVolumeType` so we can toggle on/off for AWS LZ deployments
- Rewrote `00-sed-instance-specific-settings` config block to support the use of IMDSv2 authenticated endpoints