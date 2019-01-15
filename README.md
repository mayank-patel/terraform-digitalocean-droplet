# terraform-digitalocean-droplet
Terraform module which creates droplet(s) and optionally, block storage volumes
on DigitalOcean.

These types of resources are used:
* [DigitalOcean Droplet](https://www.terraform.io/docs/providers/do/r/droplet.html)
* [DigitalOcean Volume](https://www.terraform.io/docs/providers/do/r/volume.html)
* [DigitalOcean Volume Attachment](https://www.terraform.io/docs/providers/do/r/volume_attachment.html)

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| backups | (Optional) Boolean controlling if backups are made. Defaults to false. | string | `false` | no |
| block\_storage\_filesystem\_label | (Optional) Initial filesystem label for the block storage volume. | string | `` | no |
| block\_storage\_filesystem\_type | (Optional) Initial filesystem type (xfs or ext4) for the block storage volume. | string | `xfs` | no |
| block\_storage\_size | (Required) The size of the block storage volume in GiB. If updated, can only be expanded. | string | `40` | no |
| block\_storage\_snapshot\_id | (Optional) The ID of an existing volume snapshot from which the new volume will be created. If supplied, the region and size will be limitied on creation to that of the referenced snapshot | string | `` | no |
| custom\_image | Whether the image is custom or not (an official image) | string | `0` | no |
| domain\_external | Domain name to construct FQDN from (DigitalOcean configures PTR record if zone is hosted by them) | string | `` | no |
| droplet\_name | The name of the droplet. If more than one droplet it is appended with the count, examples: stg-web, stg-web-01, stg-web-02 | string | - | yes |
| droplet\_size | the size slug of a droplet size | string | `micro` | no |
| image\_id | The id of an image to use | string | `` | no |
| image\_name | The image name or slug to lookup | string | `ubuntu-18-04-x64` | no |
| ipv6 | (Optional) Boolean controlling if IPv6 is enabled. Defaults to false. | string | `false` | no |
| monitoring | (Optional) Boolean controlling whether monitoring agent is installed. Defaults to false. | string | `false` | no |
| number\_format | The number format used to output. | string | `%02d` | no |
| number\_of\_droplets | The number of droplets / other resources to create | string | `1` | no |
| private\_networking | (Optional) Boolean controlling if private networks are enabled. Defaults to false. | string | `false` | no |
| region | The Digitalocean datacenter to create resources in | string | `ams3` | no |
| resize\_disk | (Optional) Boolean controlling whether to increase the disk size when resizing a Droplet. It defaults to true. When set to false, only the Droplet's RAM and CPU will be resized. Increasing a Droplet's disk size is a permanent change. Increasing only RAM and CPU is reversible. | string | `true` | no |
| sizes | A map of pre-canned instance sizes | map | `{ "large": "s-6vcpu-16gb", "maximum": "s-32vcpu-192gb", "medium": "s-4vcpu-8gb", "micro": "s-2vcpu-2gb", "nano": "s-1vcpu-1gb", "small": "s-2vcpu-4gb", "x-large": "s-8vcpu-32gb", "xx-large": "s-16vcpu-64gb", "xxx-large": "s-24vcpu-128gb" }` | no |
| ssh\_keys | (Optional) A list of SSH IDs or fingerprints to enable in the format [12345, 123456]. To retrieve this info, use a tool such as curl with the DigitalOcean API, to retrieve them. | list | `[]` | no |
| tags | (Optional) A list of the tags to label this Droplet. A tag resource must exist before it can be associated with a Droplet. | list | `[]` | no |
| user\_data | (Optional) - A string of the desired User Data for the Droplet. | string | `` | no |
| volume\_ids | (Optional) - A list of the IDs of each block storage volume to be attached to the Droplet. | string | `` | no |

## Outputs

| Name | Description |
|------|-------------|
| droplet\_id | List of IDs of Droplets |
| droplet\_ids | List of associated Droplet IDs of Volumes |
| filesystem\_label | List of initial filesystem labels of Volumes |
| filesystem\_type | List of initial filesystem types of Volumes |
| image | List of images of Droplets |
| ipv4\_address | List of public IPv4 addresses assigned to the Droplets |
| ipv4\_address\_private | List of private IPv4 addresses assigned to the Droplets, if applicable |
| ipv6\_address | List of public IPv6 addresses assigned to the Droplets, if applicable |
| ipv6\_address\_private | List of private IPv6 addresses assigned to the Droplets, if applicable |
| name | List of names of Droplets |
| region | List of regions of Droplets |
| size | List of sizes of Droplets |
| tags | List of tags of Droplets |
| volume\_attachment\_id | List of IDs of Volume Attachments |
| volume\_id | List of IDs of Volumes |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
