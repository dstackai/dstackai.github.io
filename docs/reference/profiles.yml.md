# .dstack/profiles.yml

Sometimes, you may want to reuse the same parameters across runs or set your own defaults so you don’t have to repeat them in every run configuration. You can do this by defining a profile, either globally in `~/.dstack/profiles.yml` or locally in `.dstack/profiles.yml`. 

A profile can be set as `default` to apply automatically to any run, or specified with `--profile NAME` in `dstack apply`.

Example:

<div editor-title=".dstack/profiles.yml"> 

```yaml
profiles:
  - name: my-profile
    # If set to true, this profile will be applied automatically
    default: true

    # The spot pololicy can be "spot", "on-demand", or "auto"
    spot_policy: auto
    # Limit the maximum price of the instance per hour
    max_price: 1.5
    # Stop any run if it runs longer that this duration
    max_duration: 1d
    # Use only these backends
    backends: [azure, lambda]
```

</div>

The profile configuration supports most properties that a run configuration supports — see below.

### Root reference

###### `backends` - (Optional) The backends to consider for provisioning (e.g., `[aws, gcp]`).  { #backends data-toc-label='backends' class='reference-item' }
###### `regions` - (Optional) The regions to consider for provisioning (e.g., `[eu-west-1, us-west4, westeurope]`).  { #regions data-toc-label='regions' class='reference-item' }
###### `availability_zones` - (Optional) The availability zones to consider for provisioning (e.g., `[eu-west-1a, us-west4-a]`).  { #availability_zones data-toc-label='availability_zones' class='reference-item' }
###### `instance_types` - (Optional) The cloud-specific instance types to consider for provisioning (e.g., `[p3.8xlarge, n1-standard-4]`).  { #instance_types data-toc-label='instance_types' class='reference-item' }
###### `reservation` - (Optional) The existing reservation to use for instance provisioning. Supports AWS Capacity Reservations, AWS Capacity Blocks, and GCP reservations.  { #reservation data-toc-label='reservation' class='reference-item' }
###### `spot_policy` - (Optional) The policy for provisioning spot or on-demand instances: `spot`, `on-demand`, `auto`. Defaults to `on-demand`.  { #spot_policy data-toc-label='spot_policy' class='reference-item' }
###### [`retry`](#retry) - (Optional) The policy for resubmitting the run. Defaults to `false`.  { #_retry data-toc-label='retry' class='reference-item' }
###### `max_duration` - (Optional) The maximum duration of a run (e.g., `2h`, `1d`, etc) in a running state, excluding provisioning and pulling. After it elapses, the run is automatically stopped. Use `off` for unlimited duration. Defaults to `off`.  { #max_duration data-toc-label='max_duration' class='reference-item' }
###### `stop_duration` - (Optional) The maximum duration of a run graceful stopping. After it elapses, the run is automatically forced stopped. This includes force detaching volumes used by the run. Use `off` for unlimited duration. Defaults to `5m`.  { #stop_duration data-toc-label='stop_duration' class='reference-item' }
###### `max_price` - (Optional) The maximum instance price per hour, in dollars.  { #max_price data-toc-label='max_price' class='reference-item' }
###### `creation_policy` - (Optional) The policy for using instances from fleets: `reuse`, `reuse-or-create`. Defaults to `reuse-or-create`.  { #creation_policy data-toc-label='creation_policy' class='reference-item' }
###### `idle_duration` - (Optional) Time to wait before terminating idle instances. Instances are not terminated if the fleet is already at `nodes.min`. Defaults to `5m` for runs and `3d` for fleets. Use `off` for unlimited duration.  { #idle_duration data-toc-label='idle_duration' class='reference-item' }
###### [`utilization_policy`](#utilization_policy) - (Optional) Run termination policy based on utilization.  { #_utilization_policy data-toc-label='utilization_policy' class='reference-item' }
###### `startup_order` - (Optional) The order in which master and workers jobs are started: `any`, `master-first`, `workers-first`. Defaults to `any`.  { #startup_order data-toc-label='startup_order' class='reference-item' }
###### `stop_criteria` - (Optional) The criteria determining when a multi-node run should be considered finished: `all-done`, `master-done`. Defaults to `all-done`.  { #stop_criteria data-toc-label='stop_criteria' class='reference-item' }
###### [`schedule`](#schedule) - (Optional) The schedule for starting the run at specified time.  { #_schedule data-toc-label='schedule' class='reference-item' }
###### `fleets` - (Optional) The fleets considered for reuse.  { #fleets data-toc-label='fleets' class='reference-item' }
###### `tags` - (Optional) The custom tags to associate with the resource. The tags are also propagated to the underlying backend resources. If there is a conflict with backend-level tags, does not override them.  { #tags data-toc-label='tags' class='reference-item' }
###### `name` - (Optional) The name of the profile that can be passed as `--profile` to `dstack apply`.  { #name data-toc-label='name' class='reference-item' }
###### `default` - (Optional) If set to true, `dstack apply` will use this profile by default..  { #default data-toc-label='default' class='reference-item' }


### `retry`

###### `on_events` - (Optional) The list of events that should be handled with retry. Supported events are `no-capacity`, `interruption`, `error`. Omit to retry on all events.  { #on_events data-toc-label='on_events' class='reference-item' }
###### `duration` - (Optional) The maximum period of retrying the run, e.g., `4h` or `1d`. The period is calculated as a run age for `no-capacity` event and as a time passed since the last `interruption` and `error` for `interruption` and `error` events..  { #duration data-toc-label='duration' class='reference-item' }


### `utilization_policy`

###### `min_gpu_utilization` -  Minimum required GPU utilization, percent. If any GPU has utilization below specified value during the whole time window, the run is terminated.  { #min_gpu_utilization data-toc-label='min_gpu_utilization' class='reference-item' }
###### `time_window` -  The time window of metric samples taking into account to measure utilization (e.g., `30m`, `1h`). Minimum is `5m`.  { #time_window data-toc-label='time_window' class='reference-item' }

