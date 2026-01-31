# `fleet`

The `fleet` configuration type allows creating and updating fleets.

## Root reference

###### `name` - (Optional) The fleet name.  { #name data-toc-label='name' class='reference-item' }
###### [`env`](#env) - (Optional) The mapping or the list of environment variables.  { #_env data-toc-label='env' class='reference-item' }
###### [`ssh_config`](#ssh_config) - (Optional) The parameters for adding instances via SSH.  { #_ssh_config data-toc-label='ssh_config' class='reference-item' }
###### [`nodes`](#nodes) - (Optional) The number of instances in cloud fleet.  { #_nodes data-toc-label='nodes' class='reference-item' }
###### `placement` - (Optional) The placement of instances: `any` or `cluster`.  { #placement data-toc-label='placement' class='reference-item' }
###### `reservation` - (Optional) The existing reservation to use for instance provisioning. Supports AWS Capacity Reservations, AWS Capacity Blocks, and GCP reservations.  { #reservation data-toc-label='reservation' class='reference-item' }
###### [`resources`](#resources) - (Optional) The resources requirements.  { #_resources data-toc-label='resources' class='reference-item' }
###### `blocks` - (Optional) The amount of blocks to split the instance into, a number or `auto`. `auto` means as many as possible. The number of GPUs and CPUs must be divisible by the number of blocks. Defaults to `1`, i.e. do not split. Defaults to `1`. { #blocks data-toc-label='blocks' class='reference-item' }
###### `backends` - (Optional) The backends to consider for provisioning (e.g., `[aws, gcp]`).  { #backends data-toc-label='backends' class='reference-item' }
###### `regions` - (Optional) The regions to consider for provisioning (e.g., `[eu-west-1, us-west4, westeurope]`).  { #regions data-toc-label='regions' class='reference-item' }
###### `availability_zones` - (Optional) The availability zones to consider for provisioning (e.g., `[eu-west-1a, us-west4-a]`).  { #availability_zones data-toc-label='availability_zones' class='reference-item' }
###### `instance_types` - (Optional) The cloud-specific instance types to consider for provisioning (e.g., `[p3.8xlarge, n1-standard-4]`).  { #instance_types data-toc-label='instance_types' class='reference-item' }
###### `spot_policy` - (Optional) The policy for provisioning spot or on-demand instances: `spot`, `on-demand`, `auto`. Defaults to `on-demand`.  { #spot_policy data-toc-label='spot_policy' class='reference-item' }
###### [`retry`](#retry) - (Optional) The policy for provisioning retry. Defaults to `false`.  { #_retry data-toc-label='retry' class='reference-item' }
###### `max_price` - (Optional) The maximum instance price per hour, in dollars.  { #max_price data-toc-label='max_price' class='reference-item' }
###### `idle_duration` - (Optional) Time to wait before terminating idle instances. Instances are not terminated if the fleet is already at `nodes.min`. Defaults to `5m` for runs and `3d` for fleets. Use `off` for unlimited duration.  { #idle_duration data-toc-label='idle_duration' class='reference-item' }
###### `tags` - (Optional) The custom tags to associate with the resource. The tags are also propagated to the underlying backend resources. If there is a conflict with backend-level tags, does not override them.  { #tags data-toc-label='tags' class='reference-item' }


### `ssh_config` { data-toc-label="ssh_config" }

###### `user` - (Optional) The user to log in with on all hosts.  { #user data-toc-label='user' class='reference-item' }
###### `port` - (Optional) The SSH port to connect to.  { #port data-toc-label='port' class='reference-item' }
###### `identity_file` - (Optional) The private key to use for all hosts.  { #identity_file data-toc-label='identity_file' class='reference-item' }
###### [`proxy_jump`](#ssh_config-proxy_jump) - (Optional) The SSH proxy configuration for all hosts.  { #_proxy_jump data-toc-label='proxy_jump' class='reference-item' }
###### `hosts` -  The per host connection parameters: a hostname or an object that overrides default ssh parameters.  { #hosts data-toc-label='hosts' class='reference-item' }
###### `network` - (Optional) The network address for cluster setup in the format `<ip>/<netmask>`. `dstack` will use IP addresses from this network for communication between hosts. If not specified, `dstack` will use IPs from the first found internal network..  { #network data-toc-label='network' class='reference-item' }


#### `ssh_config.proxy_jump` { #ssh_config-proxy_jump data-toc-label="proxy_jump" }

###### `hostname` -  The IP address or domain of proxy host.  { #hostname data-toc-label='hostname' class='reference-item' }
###### `port` - (Optional) The SSH port of proxy host.  { #port data-toc-label='port' class='reference-item' }
###### `user` -  The user to log in with for proxy host.  { #user data-toc-label='user' class='reference-item' }
###### `identity_file` -  The private key to use for proxy host.  { #identity_file data-toc-label='identity_file' class='reference-item' }


#### `ssh_config.hosts[n]` { #ssh_config-hosts data-toc-label="hosts" }

###### `hostname` -  The IP address or domain to connect to.  { #hostname data-toc-label='hostname' class='reference-item' }
###### `port` - (Optional) The SSH port to connect to for this host.  { #port data-toc-label='port' class='reference-item' }
###### `user` - (Optional) The user to log in with for this host.  { #user data-toc-label='user' class='reference-item' }
###### `identity_file` - (Optional) The private key to use for this host.  { #identity_file data-toc-label='identity_file' class='reference-item' }
###### [`proxy_jump`](#proxy_jump) - (Optional) The SSH proxy configuration for this host.  { #_proxy_jump data-toc-label='proxy_jump' class='reference-item' }
###### `internal_ip` - (Optional) The internal IP of the host used for communication inside the cluster. If not specified, `dstack` will use the IP address from `network` or from the first found internal network..  { #internal_ip data-toc-label='internal_ip' class='reference-item' }
###### `blocks` - (Optional) The amount of blocks to split the instance into, a number or `auto`. `auto` means as many as possible. The number of GPUs and CPUs must be divisible by the number of blocks. Defaults to `1`, i.e. do not split. Defaults to `1`. { #blocks data-toc-label='blocks' class='reference-item' }


##### `ssh_config.hosts[n].proxy_jump` { #proxy_jump data-toc-label="hosts[n].proxy_jump" }

###### `hostname` -  The IP address or domain of proxy host.  { #hostname data-toc-label='hostname' class='reference-item' }
###### `port` - (Optional) The SSH port of proxy host.  { #port data-toc-label='port' class='reference-item' }
###### `user` -  The user to log in with for proxy host.  { #user data-toc-label='user' class='reference-item' }
###### `identity_file` -  The private key to use for proxy host.  { #identity_file data-toc-label='identity_file' class='reference-item' }


### `resources`

###### [`cpu`](#resources-cpu) - (Optional) The CPU requirements.  { #_cpu data-toc-label='cpu' class='reference-item' }
###### `memory` - (Optional) The RAM size (e.g., `8GB`). Defaults to `8GB..`. { #memory data-toc-label='memory' class='reference-item' }
###### `shm_size` - (Optional) The size of shared memory (e.g., `8GB`). If you are using parallel communicating processes (e.g., dataloaders in PyTorch), you may need to configure this.  { #shm_size data-toc-label='shm_size' class='reference-item' }
###### [`gpu`](#resources-gpu) - (Optional) The GPU requirements.  { #_gpu data-toc-label='gpu' class='reference-item' }
###### [`disk`](#resources-disk) - (Optional) The disk resources.  { #_disk data-toc-label='disk' class='reference-item' }


#### `resources.cpu` { #resources-cpu data-toc-label="cpu" }

###### `arch` - (Optional) The CPU architecture, one of: `x86`, `arm`.  { #arch data-toc-label='arch' class='reference-item' }
###### `count` - (Optional) The number of CPU cores. Defaults to `2..`. { #count data-toc-label='count' class='reference-item' }


#### `resources.gpu` { #resources-gpu data-toc-label="gpu" }

###### `vendor` - (Optional) The vendor of the GPU/accelerator, one of: `nvidia`, `amd`, `google` (alias: `tpu`), `intel`.  { #vendor data-toc-label='vendor' class='reference-item' }
###### `name` - (Optional) The name of the GPU (e.g., `A100` or `H100`).  { #name data-toc-label='name' class='reference-item' }
###### `count` - (Optional) The number of GPUs. Defaults to `1..`. { #count data-toc-label='count' class='reference-item' }
###### `memory` - (Optional) The RAM size (e.g., `16GB`). Can be set to a range (e.g. `16GB..`, or `16GB..80GB`).  { #memory data-toc-label='memory' class='reference-item' }
###### `total_memory` - (Optional) The total RAM size (e.g., `32GB`). Can be set to a range (e.g. `16GB..`, or `16GB..80GB`).  { #total_memory data-toc-label='total_memory' class='reference-item' }
###### `compute_capability` - (Optional) The minimum compute capability of the GPU (e.g., `7.5`).  { #compute_capability data-toc-label='compute_capability' class='reference-item' }


#### `resources.disk` { #resources-disk data-toc-label="disk" }

###### `size` -  Disk size.  { #size data-toc-label='size' class='reference-item' }


### `retry`

###### `on_events` - (Optional) The list of events that should be handled with retry. Supported events are `no-capacity`, `interruption`, `error`. Omit to retry on all events.  { #on_events data-toc-label='on_events' class='reference-item' }
###### `duration` - (Optional) The maximum period of retrying the run, e.g., `4h` or `1d`. The period is calculated as a run age for `no-capacity` event and as a time passed since the last `interruption` and `error` for `interruption` and `error` events..  { #duration data-toc-label='duration' class='reference-item' }

