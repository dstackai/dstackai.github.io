# `volume`

The `volume` configuration type allows creating, registering, and updating [volumes](../../concepts/volumes.md).

## Root reference

###### `name` - (Optional) `str` The volume name. { #name data-toc-label='name' class='reference-item' }
###### `backend` - (Required) `"amddevcloud" | "aws" | "azure" | "cloudrift" | "cudo" | "datacrunch" | "digitalocean" | "dstack" | "gcp" | "hotaisle" | "kubernetes" | "lambda" | "local" | "remote" | "nebius" | "oci" | "runpod" | "tensordock" | "vastai" | "verda" | "vultr"` The volume backend. { #backend data-toc-label='backend' class='reference-item' }
###### `region` - (Required) `str` The volume region. { #region data-toc-label='region' class='reference-item' }
###### `availability_zone` - (Optional) `str` The volume availability zone. { #availability_zone data-toc-label='availability_zone' class='reference-item' }
###### `size` - (Optional) `str` The volume size. Must be specified when creating new volumes. { #size data-toc-label='size' class='reference-item' }
###### `volume_id` - (Optional) `str` The volume ID. Must be specified when registering external volumes. { #volume_id data-toc-label='volume_id' class='reference-item' }
###### `auto_cleanup_duration` - (Optional) `int | str` Time to wait after volume is no longer used by any job before deleting it. Defaults to keep the volume indefinitely. Use the value 'off' or -1 to disable auto-cleanup.. { #auto_cleanup_duration data-toc-label='auto_cleanup_duration' class='reference-item' }
###### `tags` - (Optional) `dict` The custom tags to associate with the volume. The tags are also propagated to the underlying backend resources. If there is a conflict with backend-level tags, does not override them. { #tags data-toc-label='tags' class='reference-item' }

