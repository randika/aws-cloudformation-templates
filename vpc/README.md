VPC templates
===

# vpc-subnetprv-subnetpub.json

This template deploys a VPC, with a pair of public and private subnets spread\nacross two Availability Zones. It deploys an Internet Gateway, with a default\nroute on the public subnets. It deploys a pair of NAT Gateways (one in each AZ),\nand default routes for them in the private subnets.
