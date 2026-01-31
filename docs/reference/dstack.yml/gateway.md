# `gateway`

The `gateway` configuration type allows creating and updating [gateways](../../concepts/gateways.md).

## Root reference

###### `name` - (Optional) The gateway name.  { #name data-toc-label='name' class='reference-item' }
###### `default` - (Optional) Make the gateway default.  { #default data-toc-label='default' class='reference-item' }
###### `backend` -  The gateway backend.  { #backend data-toc-label='backend' class='reference-item' }
###### `region` -  The gateway region.  { #region data-toc-label='region' class='reference-item' }
###### `instance_type` - (Optional) Backend-specific instance type to use for the gateway instance. Omit to use the backend's default, which is typically a small non-GPU instance.  { #instance_type data-toc-label='instance_type' class='reference-item' }
###### [`router`](#router) - (Optional) The router configuration.  { #_router data-toc-label='router' class='reference-item' }
###### `domain` - (Optional) The gateway domain, e.g. `example.com`.  { #domain data-toc-label='domain' class='reference-item' }
###### `public_ip` - (Optional) Allocate public IP for the gateway. Defaults to `True`. { #public_ip data-toc-label='public_ip' class='reference-item' }
###### [`certificate`](#certificate) - (Optional) The SSL certificate configuration. Defaults to `type: lets-encrypt`.  { #_certificate data-toc-label='certificate' class='reference-item' }
###### `tags` - (Optional) The custom tags to associate with the gateway. The tags are also propagated to the underlying backend resources. If there is a conflict with backend-level tags, does not override them.  { #tags data-toc-label='tags' class='reference-item' }


### `router`

=== "SGLang Model Gateway"

    ###### `type` -  The router type. Must be `sglang`. { #type data-toc-label='type' class='reference-item' }
    ###### `policy` - (Optional) The routing policy. Options: `random`, `round_robin`, `cache_aware`, `power_of_two`. Defaults to `cache_aware`. { #policy data-toc-label='policy' class='reference-item' }


### `certificate`

=== "Let's encrypt"

    ###### `type` -  Automatic certificates by Let's Encrypt. Must be `lets-encrypt`. { #type data-toc-label='type' class='reference-item' }


=== "ACM" 

    ###### `type` -  Certificates by AWS Certificate Manager (ACM). Must be `acm`. { #type data-toc-label='type' class='reference-item' }
    ###### `arn` -  The ARN of the wildcard ACM certificate for the domain.  { #arn data-toc-label='arn' class='reference-item' }

