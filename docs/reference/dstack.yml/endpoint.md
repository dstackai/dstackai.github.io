# `endpoint`

The `endpoint` configuration type describes a model request and the constraints
used to create or apply an [endpoint preset](../../concepts/endpoints.md).

## Root reference

###### `backends` - (Optional) `list["amddevcloud" | "aws" | "azure" | "cloudrift" | "crusoe" | "cudo" | "datacrunch" | "digitalocean" | "dstack" | "gcp" | "hotaisle" | "jarvislabs" | "kubernetes" | "lambda" | "remote" | "nebius" | "oci" | "runpod" | "tensordock" | "vastai" | "verda" | "vultr" | "slurm"]` The backends to consider for provisioning (e.g., `[aws, gcp]`). { #backends data-toc-label='backends' class='reference-item' }
###### `regions` - (Optional) `list[str]` The regions to consider for provisioning (e.g., `[eu-west-1, us-west4, westeurope]`). { #regions data-toc-label='regions' class='reference-item' }
###### `availability_zones` - (Optional) `list[str]` The availability zones to consider for provisioning (e.g., `[eu-west-1a, us-west4-a]`). { #availability_zones data-toc-label='availability_zones' class='reference-item' }
###### `instance_types` - (Optional) `list[str]` The cloud-specific instance types to consider for provisioning (e.g., `[g6e.24xlarge, n1-standard-4]`). { #instance_types data-toc-label='instance_types' class='reference-item' }
###### `reservation` - (Optional) `str` The existing reservation to use for instance provisioning. Supports AWS Capacity Reservations, AWS Capacity Blocks, and GCP reservations. { #reservation data-toc-label='reservation' class='reference-item' }
###### `spot_policy` - (Optional) `"auto" | "on-demand" | "spot"` The policy for provisioning spot or on-demand instances: `spot`, `on-demand`, `auto`. Defaults to `on-demand`. { #spot_policy data-toc-label='spot_policy' class='reference-item' }
###### [`retry`](#retry) - (Optional) `bool | object` The policy for resubmitting the run. Defaults to `false`. { #_retry data-toc-label='retry' class='reference-item' }
###### `max_duration` - (Optional) `int | str | "off"` The maximum duration of a run (e.g., `2h`, `1d`, etc) in a running state, excluding provisioning and pulling. After it elapses, the run is automatically stopped. Use `off` for unlimited duration. Defaults to `off`. { #max_duration data-toc-label='max_duration' class='reference-item' }
###### `stop_duration` - (Optional) `int | str | "off"` The maximum duration of a run graceful stopping. After it elapses, the run is automatically forced stopped. This includes force detaching volumes used by the run. Use `off` for unlimited duration. Defaults to `5m`. { #stop_duration data-toc-label='stop_duration' class='reference-item' }
###### `max_price` - (Optional) `float` The maximum instance price per hour, in dollars. { #max_price data-toc-label='max_price' class='reference-item' }
###### `creation_policy` - (Optional) `"reuse" | "reuse-or-create"` The policy for using instances from fleets: `reuse`, `reuse-or-create`. Defaults to `reuse-or-create`. { #creation_policy data-toc-label='creation_policy' class='reference-item' }
###### `idle_duration` - (Optional) `int | str` Time to wait before terminating idle instances. When the run reuses an existing fleet instance, the fleet's `idle_duration` applies. When the run provisions a new instance, the shorter of the fleet's and run's values is used. Defaults to `5m` for runs and `3d` for fleets. Use `off` for unlimited duration. Only applied for VM-based backends. { #idle_duration data-toc-label='idle_duration' class='reference-item' }
###### [`utilization_policy`](#utilization_policy) - (Optional) `object` Run termination policy based on utilization. { #_utilization_policy data-toc-label='utilization_policy' class='reference-item' }
###### `startup_order` - (Optional) `"any" | "master-first" | "workers-first"` The order in which master and workers jobs are started: `any`, `master-first`, `workers-first`. Defaults to `any`. { #startup_order data-toc-label='startup_order' class='reference-item' }
###### `stop_criteria` - (Optional) `"all-done" | "master-done"` The criteria determining when a multi-node run should be considered finished: `all-done`, `master-done`. Defaults to `all-done`. { #stop_criteria data-toc-label='stop_criteria' class='reference-item' }
###### [`schedule`](#schedule) - (Optional) `object` The schedule for starting the run at specified time. { #_schedule data-toc-label='schedule' class='reference-item' }
###### `fleets` - (Optional) `list[str | object]` The fleets considered for reuse. For fleets owned by the current project, specify fleet names. For imported fleets, specify `<project name>/<fleet name>`. { #fleets data-toc-label='fleets' class='reference-item' }
###### `instances` - (Optional) `list` The specific fleet instances to consider for reuse. Each value can be an instance name string, or an object with `name`, `hostname`, or `fleet` and `instance`. When set, the run is only placed on matching existing instances.. { #instances data-toc-label='instances' class='reference-item' }
###### `tags` - (Optional) `dict` The custom tags to associate with the resource. The tags are also propagated to the underlying backend resources. If there is a conflict with backend-level tags, does not override them. { #tags data-toc-label='tags' class='reference-item' }
###### `backend_options` - (Optional) `list[object]` Backend-specific options, applied only to offers from that backend. { #backend_options data-toc-label='backend_options' class='reference-item' }
###### `type` - (Required) `"endpoint"` The configuration type. Must be `endpoint`. { #type data-toc-label='type' class='reference-item' }
###### `name` - (Optional) `str` The endpoint name. Required unless passed with `--name`. { #name data-toc-label='name' class='reference-item' }
###### [`model`](#model) - (Required) `str | object` The model to serve. Use a string or `repo` for an exact repo/path, or `base` to allow compatible model variants.. { #_model data-toc-label='model' class='reference-item' }
###### `context_length` - (Optional) `int` The minimum required context length. { #context_length data-toc-label='context_length' class='reference-item' }
###### `preset` - (Optional) `str` The preset ID to use when applying the endpoint. { #preset data-toc-label='preset' class='reference-item' }
###### `gateway` - (Optional) `bool | str | object` The name of the gateway. Specify boolean `false` to run without a gateway. Specify boolean `true` to run with the default gateway. Omit to run with the default gateway if there is one, or without a gateway otherwise. { #gateway data-toc-label='gateway' class='reference-item' }
###### [`env`](#env) - (Optional) `list[str] | dict` The mapping or the list of environment variables. { #_env data-toc-label='env' class='reference-item' }


### `model`

=== "Base model"

    Allows the creation agent to select a compatible model variant.

    ###### `base` - (Required) `str` The base model for which the agent may select a compatible variant. { #base data-toc-label='base' class='reference-item' }


=== "Exact model"

    Requires an exact model repo or path and optionally sets another
    client-facing model name.

    ###### `repo` - (Required) `str` The exact model repo or path to deploy. { #repo data-toc-label='repo' class='reference-item' }
    ###### `name` - (Optional) `str` The client-facing model name. Defaults to `repo`. { #name data-toc-label='name' class='reference-item' }


### `retry`

###### `on_events` - (Optional) `list["no-capacity" | "interruption" | "error"]` The list of events that should be handled with retry. Supported events are `no-capacity`, `interruption`, `error`. Omit to retry on all events. { #on_events data-toc-label='on_events' class='reference-item' }
###### `duration` - (Optional) `int | str` The maximum period of retrying the run, e.g., `4h` or `1d`. The period is calculated as a run age for `no-capacity` event and as a time passed since the last `interruption` and `error` for `interruption` and `error` events.. { #duration data-toc-label='duration' class='reference-item' }


### `utilization_policy`

###### `min_gpu_utilization` - (Required) `int` Minimum required GPU utilization, percent. If any GPU has utilization below specified value during the whole time window, the run is terminated. { #min_gpu_utilization data-toc-label='min_gpu_utilization' class='reference-item' }
###### `time_window` - (Required) `int | str` The time window of metric samples taking into account to measure utilization (e.g., `30m`, `1h`). Minimum is `5m`. { #time_window data-toc-label='time_window' class='reference-item' }


### `schedule`

###### `cron` - (Required) `str | list[str]` A cron expression or a list of cron expressions specifying the UTC time when the run needs to be started. { #cron data-toc-label='cron' class='reference-item' }


### `instances[n]` { #_instances data-toc-label="instances" }

When `instances` is set, the run is placed only on matching existing fleet instances.

=== "By name"

    ###### `name` - (Required) `str` The fleet instance name. { #name data-toc-label='name' class='reference-item' }


=== "By hostname"

    ###### `hostname` - (Required) `str` The fleet instance hostname or IP address. { #hostname data-toc-label='hostname' class='reference-item' }


=== "By fleet and instance number"

    ###### [`fleet`](#fleet) - (Required) `str | object` The fleet reference. For fleets owned by the current project, specify the fleet name. For a fleet from another project, specify `<project name>/<fleet name>` or an object with `project` and `name`.. { #_fleet data-toc-label='fleet' class='reference-item' }
    ###### `instance` - (Required) `int` The fleet instance number. { #instance data-toc-label='instance' class='reference-item' }


??? info "Short syntax"

    The short syntax for instances is an instance name string.

    * `my-fleet-1`, same as `{name: my-fleet-1}`

### `backend_options`

Backend-specific options that only take effect for offers of the respective backend.

#### `backend_options[n][type=vastai]` { #backend_options-vastai data-toc-label="vastai" }

###### `offer_order` - (Optional) `"price" | "score"` Controls the order in which offers are considered for provisioning. Use `score` to prioritize the highest overall score first (the default order in the Vast.ai console), or `price` to prioritize the lowest-cost offers first. Lower-cost offers are often less reliable, so consider applying stricter filters when using `price`. Defaults to `score`. { #offer_order data-toc-label='offer_order' class='reference-item' }
###### `min_reliability` - (Optional) `float` The minimum reliability threshold for offers, on a scale from `0` to `1`. Defaults to `0.9`. { #min_reliability data-toc-label='min_reliability' class='reference-item' }
###### `min_score` - (Optional) `int` The minimum overall score required for offers to be considered. The scoring scale varies and may require experimentation. Starting with a value in the low hundreds is generally recommended. { #min_score data-toc-label='min_score' class='reference-item' }

