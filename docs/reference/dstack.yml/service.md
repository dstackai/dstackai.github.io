# `service`

The `service` configuration type allows running [services](../../concepts/services.md).

## Root reference

###### `port` -  The port the application listens on.  { #port data-toc-label='port' class='reference-item' }
###### `gateway` - (Optional) The name of the gateway. Specify boolean `false` to run without a gateway. Specify boolean `true` to run with the default gateway. Omit to run with the default gateway if there is one, or without a gateway otherwise.  { #gateway data-toc-label='gateway' class='reference-item' }
###### `strip_prefix` - (Optional) Strip the `/proxy/services/<project name>/<run name>/` path prefix when forwarding requests to the service. Only takes effect when running the service without a gateway. Defaults to `True`. { #strip_prefix data-toc-label='strip_prefix' class='reference-item' }
###### `model` - (Optional) Mapping of the model for the OpenAI-compatible endpoint provided by `dstack`. Can be a full model format definition or just a model name. If it's a name, the service is expected to expose an OpenAI-compatible API at the `/v1` path.  { #model data-toc-label='model' class='reference-item' }
###### `https` - (Optional) Enable HTTPS if running with a gateway. Defaults to `True`. { #https data-toc-label='https' class='reference-item' }
###### `auth` - (Optional) Enable the authorization. Defaults to `True`. { #auth data-toc-label='auth' class='reference-item' }
###### [`scaling`](#scaling) - (Optional) The auto-scaling rules. Required if `replicas` is set to a range.  { #_scaling data-toc-label='scaling' class='reference-item' }
###### [`rate_limits`](#rate_limits) - (Optional) Rate limiting rules.  { #_rate_limits data-toc-label='rate_limits' class='reference-item' }
###### [`probes`](#probes) - (Optional) List of probes used to determine job health.  { #_probes data-toc-label='probes' class='reference-item' }
###### `replicas` - (Optional) The number of replicas or a list of replica groups. Can be an integer (e.g., `2`), a range (e.g., `0..4`), or a list of replica groups. Each replica group defines replicas with shared configuration (commands, resources, scaling). When `replicas` is a list of replica groups, top-level `scaling`, `commands`, and `resources` are not allowed and must be specified in each replica group instead. .  { #replicas data-toc-label='replicas' class='reference-item' }
###### `commands` - (Optional) The shell commands to run.  { #commands data-toc-label='commands' class='reference-item' }
###### `name` - (Optional) The run name. If not specified, a random name is generated.  { #name data-toc-label='name' class='reference-item' }
###### `image` - (Optional) The name of the Docker image to run.  { #image data-toc-label='image' class='reference-item' }
###### `user` - (Optional) The user inside the container, `user_name_or_id[:group_name_or_id]` (e.g., `ubuntu`, `1000:1000`). Defaults to the default user from the `image`.  { #user data-toc-label='user' class='reference-item' }
###### `privileged` - (Optional) Run the container in privileged mode.  { #privileged data-toc-label='privileged' class='reference-item' }
###### `entrypoint` - (Optional) The Docker entrypoint.  { #entrypoint data-toc-label='entrypoint' class='reference-item' }
###### `working_dir` - (Optional) The absolute path to the working directory inside the container. Defaults to the `image`'s default working directory.  { #working_dir data-toc-label='working_dir' class='reference-item' }
###### [`registry_auth`](#registry_auth) - (Optional) Credentials for pulling a private Docker image.  { #_registry_auth data-toc-label='registry_auth' class='reference-item' }
###### `python` - (Optional) The major version of Python. Mutually exclusive with `image` and `docker`.  { #python data-toc-label='python' class='reference-item' }
###### `nvcc` - (Optional) Use image with NVIDIA CUDA Compiler (NVCC) included. Mutually exclusive with `image` and `docker`.  { #nvcc data-toc-label='nvcc' class='reference-item' }
###### `single_branch` - (Optional) Whether to clone and track only the current branch or all remote branches. Relevant only when using remote Git repos. Defaults to `false` for dev environments and to `true` for tasks and services.  { #single_branch data-toc-label='single_branch' class='reference-item' }
###### [`env`](#env) - (Optional) The mapping or the list of environment variables.  { #_env data-toc-label='env' class='reference-item' }
###### `shell` - (Optional) The shell used to run commands. Allowed values are `sh`, `bash`, or an absolute path, e.g., `/usr/bin/zsh`. Defaults to `/bin/sh` if the `image` is specified, `/bin/bash` otherwise.  { #shell data-toc-label='shell' class='reference-item' }
###### [`resources`](#resources) - (Optional) The resources requirements to run the configuration.  { #_resources data-toc-label='resources' class='reference-item' }
###### `priority` - (Optional) The priority of the run, an integer between `0` and `100`. `dstack` tries to provision runs with higher priority first. Defaults to `0`.  { #priority data-toc-label='priority' class='reference-item' }
###### `volumes` - (Optional) The volumes mount points.  { #volumes data-toc-label='volumes' class='reference-item' }
###### `docker` - (Optional) Use Docker inside the container. Mutually exclusive with `image`, `python`, and `nvcc`. Overrides `privileged`.  { #docker data-toc-label='docker' class='reference-item' }
###### [`repos`](#repos) - (Optional) The list of Git repos.  { #_repos data-toc-label='repos' class='reference-item' }
###### [`files`](#files) - (Optional) The local to container file path mappings.  { #_files data-toc-label='files' class='reference-item' }
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


### `model` { data-toc-label="model" }

=== "OpenAI"

    ###### `type` -  The type of the model. Must be `chat`. { #type data-toc-label='type' class='reference-item' }
    ###### `name` -  The name of the model.  { #name data-toc-label='name' class='reference-item' }
    ###### `format` -  The serving format. Must be set to `openai`.  { #format data-toc-label='format' class='reference-item' }
    ###### `prefix` - (Optional) The `base_url` prefix (after hostname). Defaults to `/v1`. { #prefix data-toc-label='prefix' class='reference-item' }


=== "TGI"

    > TGI provides an OpenAI-compatible API starting with version 1.4.0,
    so models served by TGI can be defined with `format: openai` too.

    ###### `type` -  The type of the model. Must be `chat`. { #type data-toc-label='type' class='reference-item' }
    ###### `name` -  The name of the model.  { #name data-toc-label='name' class='reference-item' }
    ###### `format` -  The serving format. Must be set to `tgi`.  { #format data-toc-label='format' class='reference-item' }
    ###### `chat_template` - (Optional) The custom prompt template for the model. If not specified, the default prompt template from the HuggingFace Hub configuration will be used.  { #chat_template data-toc-label='chat_template' class='reference-item' }
    ###### `eos_token` - (Optional) The custom end of sentence token. If not specified, the default end of sentence token from the HuggingFace Hub configuration will be used.  { #eos_token data-toc-label='eos_token' class='reference-item' }


    ??? info "Chat template"

        By default, `dstack` loads the [chat template](https://huggingface.co/docs/transformers/main/en/chat_templating)
        from the model's repository. If it is not present there, manual configuration is required.

        ```yaml
        type: service

        image: ghcr.io/huggingface/text-generation-inference:latest
        env:
          - MODEL_ID=TheBloke/Llama-2-13B-chat-GPTQ
        commands:
          - text-generation-launcher --port 8000 --trust-remote-code --quantize gptq
        port: 8000

        resources:
          gpu: 80GB

        # Enable the OpenAI-compatible endpoint
        model:
          type: chat
          name: TheBloke/Llama-2-13B-chat-GPTQ
          format: tgi
          chat_template: "{% if messages[0]['role'] == 'system' %}{% set loop_messages = messages[1:] %}{% set system_message = messages[0]['content'] %}{% else %}{% set loop_messages = messages %}{% set system_message = false %}{% endif %}{% for message in loop_messages %}{% if (message['role'] == 'user') != (loop.index0 % 2 == 0) %}{{ raise_exception('Conversation roles must alternate user/assistant/user/assistant/...') }}{% endif %}{% if loop.index0 == 0 and system_message != false %}{% set content = '<<SYS>>\\n' + system_message + '\\n<</SYS>>\\n\\n' + message['content'] %}{% else %}{% set content = message['content'] %}{% endif %}{% if message['role'] == 'user' %}{{ '<s>[INST] ' + content.strip() + ' [/INST]' }}{% elif message['role'] == 'assistant' %}{{ ' '  + content.strip() + ' </s>' }}{% endif %}{% endfor %}"
          eos_token: "</s>"
        ```

        Please note that model mapping is an experimental feature with the following limitations:

        1. Doesn't work if your `chat_template` uses `bos_token`. As a workaround, replace `bos_token` inside `chat_template` with the token content itself.
        2. Doesn't work if `eos_token` is defined in the model repository as a dictionary. As a workaround, set `eos_token` manually, as shown in the example above (see Chat template).

        If you encounter any other issues, please make sure to file a
        [GitHub issue](https://github.com/dstackai/dstack/issues/new/choose).

### `scaling`

###### `metric` -  The target metric to track. Currently, the only supported value is `rps` (meaning requests per second).  { #metric data-toc-label='metric' class='reference-item' }
###### `target` -  The target value of the metric. The number of replicas is calculated based on this number and automatically adjusts (scales up or down) as this metric changes.  { #target data-toc-label='target' class='reference-item' }
###### `scale_up_delay` - (Optional) The delay in seconds before scaling up. Defaults to `300`. { #scale_up_delay data-toc-label='scale_up_delay' class='reference-item' }
###### `scale_down_delay` - (Optional) The delay in seconds before scaling down. Defaults to `600`. { #scale_down_delay data-toc-label='scale_down_delay' class='reference-item' }


### `rate_limits`

#### `rate_limits[n]`

###### `prefix` - (Optional) URL path prefix to which this limit is applied. If an incoming request matches several prefixes, the longest prefix is applied. Defaults to `/`. { #prefix data-toc-label='prefix' class='reference-item' }
###### [`key`](#key) - (Optional) The partitioning key. Each incoming request belongs to a partition and rate limits are applied per partition. Defaults to partitioning by client IP address.  { #_key data-toc-label='key' class='reference-item' }
###### `rps` -  Max allowed number of requests per second. Requests are tracked at millisecond granularity. For example, `rps: 10` means at most 1 request per 100ms.  { #rps data-toc-label='rps' class='reference-item' }
###### `burst` - (Optional) Max number of requests that can be passed to the service ahead of the rate limit.  { #burst data-toc-label='burst' class='reference-item' }


##### `rate_limits[n].key` { data-toc-label="key" }

=== "IP address"

    Partition requests by client IP address.

    ###### `type` -  Partitioning type. Must be `ip_address`. { #type data-toc-label='type' class='reference-item' }


=== "Header"

    Partition requests by the value of a header.

    ###### `type` -  Partitioning type. Must be `header`. { #type data-toc-label='type' class='reference-item' }
    ###### `header` -  Name of the header to use for partitioning.  { #header data-toc-label='header' class='reference-item' }


### `probes`

#### `probes[n]`

###### `url` - (Optional) The URL to request. Defaults to `/`.  { #url data-toc-label='url' class='reference-item' }
###### `method` - (Optional) The HTTP method to use for the probe (e.g., `get`, `post`, etc.). Defaults to `get`.  { #method data-toc-label='method' class='reference-item' }
###### `headers` - (Optional) A list of HTTP headers to include in the request.  { #headers data-toc-label='headers' class='reference-item' }
###### `body` - (Optional) The HTTP request body to send with the probe.  { #body data-toc-label='body' class='reference-item' }
###### `timeout` - (Optional) Maximum amount of time the HTTP request is allowed to take. Defaults to `10s`.  { #timeout data-toc-label='timeout' class='reference-item' }
###### `interval` - (Optional) Minimum amount of time between the end of one probe execution and the start of the next. Defaults to `15s`.  { #interval data-toc-label='interval' class='reference-item' }
###### `ready_after` - (Optional) The number of consecutive successful probe executions required for the replica to be considered ready. Used during rolling deployments. Defaults to `1`.  { #ready_after data-toc-label='ready_after' class='reference-item' }


##### `probes[n].headers`

###### `probes[n].headers[m]`

###### `name` -  The name of the HTTP header.  { #name data-toc-label='name' class='reference-item' }
###### `value` -  The value of the HTTP header.  { #value data-toc-label='value' class='reference-item' }



### `retry`

###### `on_events` - (Optional) The list of events that should be handled with retry. Supported events are `no-capacity`, `interruption`, `error`. Omit to retry on all events.  { #on_events data-toc-label='on_events' class='reference-item' }
###### `duration` - (Optional) The maximum period of retrying the run, e.g., `4h` or `1d`. The period is calculated as a run age for `no-capacity` event and as a time passed since the last `interruption` and `error` for `interruption` and `error` events..  { #duration data-toc-label='duration' class='reference-item' }


### `utilization_policy`

###### `min_gpu_utilization` -  Minimum required GPU utilization, percent. If any GPU has utilization below specified value during the whole time window, the run is terminated.  { #min_gpu_utilization data-toc-label='min_gpu_utilization' class='reference-item' }
###### `time_window` -  The time window of metric samples taking into account to measure utilization (e.g., `30m`, `1h`). Minimum is `5m`.  { #time_window data-toc-label='time_window' class='reference-item' }


### `schedule`

###### `cron` -  A cron expression or a list of cron expressions specifying the UTC time when the run needs to be started.  { #cron data-toc-label='cron' class='reference-item' }


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


### `registry_auth`

###### `username` -  The username.  { #username data-toc-label='username' class='reference-item' }
###### `password` -  The password or access token.  { #password data-toc-label='password' class='reference-item' }


### `volumes[n]` { #_volumes data-toc-label="volumes" }

=== "Network volumes"

    ###### `name` -  The network volume name or the list of network volume names to mount. If a list is specified, one of the volumes in the list will be mounted. Specify volumes from different backends/regions to increase availability.  { #name data-toc-label='name' class='reference-item' }
    ###### `path` -  The absolute container path to mount the volume at.  { #path data-toc-label='path' class='reference-item' }


=== "Instance volumes"

    ###### `instance_path` -  The absolute path on the instance (host).  { #instance_path data-toc-label='instance_path' class='reference-item' }
    ###### `path` -  The absolute path in the container.  { #path data-toc-label='path' class='reference-item' }
    ###### `optional` - (Optional) Allow running without this volume in backends that do not support instance volumes.  { #optional data-toc-label='optional' class='reference-item' }


??? info "Short syntax"

    The short syntax for volumes is a colon-separated string in the form of `source:destination`

    * `volume-name:/container/path` for network volumes
    * `/instance/path:/container/path` for instance volumes

### `repos[n]` { #_repos data-toc-label="repos" }

> Currently, a maximum of one repo is supported.

> Either `local_path` or `url` must be specified.

###### `local_path` - (Optional) The path to the Git repo on the user's machine. Relative paths are resolved relative to the parent directory of the the configuration file. Mutually exclusive with `url`.  { #local_path data-toc-label='local_path' class='reference-item' }
###### `url` - (Optional) The Git repo URL. Mutually exclusive with `local_path`.  { #url data-toc-label='url' class='reference-item' }
###### `branch` - (Optional) The repo branch. Defaults to the active branch for local paths and the default branch for URLs.  { #branch data-toc-label='branch' class='reference-item' }
###### `hash` - (Optional) The commit hash.  { #hash data-toc-label='hash' class='reference-item' }
###### `path` - (Optional) The repo path inside the run container. Relative paths are resolved relative to the working directory. Defaults to `.`. { #path data-toc-label='path' class='reference-item' }
###### `if_exists` - (Optional) The action to be taken if `path` exists and is not empty. One of: `error`, `skip`. Defaults to `error`. { #if_exists data-toc-label='if_exists' class='reference-item' }


??? info "`if_exists` action"

    If the `path` already exists and is a non-empty directory, by default the run is terminated with an error.
    This can be changed with the `if_exists` option:

    * `error` – do not try to check out, terminate the run with an error (the default action since `0.20.0`)
    * `skip` – do not try to check out, skip the repo (the only action available before `0.20.0`)

    Note, if the `path` exists and is _not_ a directory (e.g., a regular file), this is always an error that
    cannot be ignored with the `skip` action.

??? info "Short syntax"

    The short syntax for repos is a colon-separated string in the form of `local_path_or_url:path`.

    * `.:/repo`
    * `..:repo`
    * `~/repos/demo:~/repo`
    * `https://github.com/org/repo:~/data/repo`
    * `git@github.com:org/repo.git:data/repo`

### `files[n]` { #_files data-toc-label="files" }

###### `local_path` -  The path on the user's machine. Relative paths are resolved relative to the parent directory of the the configuration file.  { #local_path data-toc-label='local_path' class='reference-item' }
###### `path` -  The path in the container. Relative paths are resolved relative to the working directory.  { #path data-toc-label='path' class='reference-item' }


??? info "Short syntax"

    The short syntax for files is a colon-separated string in the form of `local_path[:path]` where
    `path` is optional and can be omitted if it's equal to `local_path`.

    * `~/.bashrc`, same as `~/.bashrc:~/.bashrc`
    * `/opt/myorg`, same as `/opt/myorg/` and `/opt/myorg:/opt/myorg`
    * `libs/patched_libibverbs.so.1:/lib/x86_64-linux-gnu/libibverbs.so.1`
