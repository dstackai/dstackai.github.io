# ~/.dstack/server/config.yml

The `~/.dstack/server/config.yml` file is used
to configure [backends](../../concepts/backends.md) and other [server-level settings](../../guides/server-deployment.md).

## Root reference

###### [`projects`](#projects) -  The list of projects.  { #_projects data-toc-label='projects' class='reference-item' }
###### [`encryption`](#encryption) - (Optional) The encryption config.  { #_encryption data-toc-label='encryption' class='reference-item' }
###### [`default_permissions`](#default_permissions) - (Optional) The default user permissions.  { #_default_permissions data-toc-label='default_permissions' class='reference-item' }
###### `plugins` - (Optional) The server-side plugins to enable.  { #plugins data-toc-label='plugins' class='reference-item' }


### `projects[n]` { #projects data-toc-label="projects" }

###### `name` -  The name of the project.  { #name data-toc-label='name' class='reference-item' }
###### `backends` - (Optional) The list of backends.  { #backends data-toc-label='backends' class='reference-item' }


#### `projects[n].backends` { #backends data-toc-label="backends" }

##### `projects[n].backends[type=aws]` { #aws data-toc-label="aws" }

###### `type` -  The type of the backend. Must be `aws`. { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of AWS regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### `vpc_name` - (Optional) The name of custom VPCs. All configured regions must have a VPC with this name. If your custom VPCs don't have names or have different names in different regions, use `vpc_ids` instead..  { #vpc_name data-toc-label='vpc_name' class='reference-item' }
###### `vpc_ids` - (Optional) The mapping from AWS regions to VPC IDs. If `default_vpcs: true`, omitted regions will use default VPCs.  { #vpc_ids data-toc-label='vpc_ids' class='reference-item' }
###### `default_vpcs` - (Optional) A flag to enable/disable using default VPCs in regions not configured by `vpc_ids`. Set to `false` if default VPCs should never be used. Defaults to `true`.  { #default_vpcs data-toc-label='default_vpcs' class='reference-item' }
###### `public_ips` - (Optional) A flag to enable/disable public IP assigning on instances. `public_ips: false` requires at least one private subnet with outbound internet connectivity provided by a NAT Gateway or a Transit Gateway. Defaults to `true`.  { #public_ips data-toc-label='public_ips' class='reference-item' }
###### `iam_instance_profile` - (Optional) The name of the IAM instance profile to associate with EC2 instances. You can also specify the IAM role name for roles created via the AWS console. AWS automatically creates an instance profile and gives it the same name as the role.  { #iam_instance_profile data-toc-label='iam_instance_profile' class='reference-item' }
###### `tags` - (Optional) The tags that will be assigned to resources created by `dstack`.  { #tags data-toc-label='tags' class='reference-item' }
###### [`os_images`](#aws-os_images) - (Optional) The mapping of instance categories (CPU, NVIDIA GPU) to AMI configurations.  { #_os_images data-toc-label='os_images' class='reference-item' }
###### [`creds`](#aws-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=aws].creds` { #aws-creds data-toc-label="creds" }

=== "Access key"
    ###### `type` -  The type of credentials. Must be `access_key`. { #type data-toc-label='type' class='reference-item' }
    ###### `access_key` -  The access key.  { #access_key data-toc-label='access_key' class='reference-item' }
    ###### `secret_key` -  The secret key.  { #secret_key data-toc-label='secret_key' class='reference-item' }


=== "Default"
    ###### `type` -  The type of credentials. Must be `default`. { #type data-toc-label='type' class='reference-item' }


###### `projects[n].backends[type=aws].os_images` { #aws-os_images data-toc-label="os_images" }

###### [`cpu`](#aws-os_images-cpu) - (Optional) The AMI used for CPU instances.  { #_cpu data-toc-label='cpu' class='reference-item' }
###### [`nvidia`](#aws-os_images-nvidia) - (Optional) The AMI used for NVIDIA GPU instances.  { #_nvidia data-toc-label='nvidia' class='reference-item' }


###### `projects[n].backends[type=aws].os_images.cpu` { #aws-os_images-cpu data-toc-label="cpu" }

###### `name` -  The AMI name.  { #name data-toc-label='name' class='reference-item' }
###### `owner` - (Optional) The AMI owner, account ID or `self`. Defaults to `self`. { #owner data-toc-label='owner' class='reference-item' }
###### `user` -  The OS user for provisioning.  { #user data-toc-label='user' class='reference-item' }


###### `projects[n].backends[type=aws].os_images.nvidia` { #aws-os_images-nvidia data-toc-label="nvidia" }

###### `name` -  The AMI name.  { #name data-toc-label='name' class='reference-item' }
###### `owner` - (Optional) The AMI owner, account ID or `self`. Defaults to `self`. { #owner data-toc-label='owner' class='reference-item' }
###### `user` -  The OS user for provisioning.  { #user data-toc-label='user' class='reference-item' }


##### `projects[n].backends[type=azure]` { #azure data-toc-label="azure" }

###### `type` -  The type of the backend. Must be `azure`. { #type data-toc-label='type' class='reference-item' }
###### `tenant_id` -  The tenant ID.  { #tenant_id data-toc-label='tenant_id' class='reference-item' }
###### `subscription_id` -  The subscription ID.  { #subscription_id data-toc-label='subscription_id' class='reference-item' }
###### `resource_group` - (Optional) The resource group for resources created by `dstack`. If not specified, `dstack` will create a new resource group.  { #resource_group data-toc-label='resource_group' class='reference-item' }
###### `regions` - (Optional) The list of Azure regions (locations). Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### `vpc_ids` - (Optional) The mapping from configured Azure locations to network IDs. A network ID must have a format `networkResourceGroup/networkName` If not specified, `dstack` will create a new network for every configured region.  { #vpc_ids data-toc-label='vpc_ids' class='reference-item' }
###### `public_ips` - (Optional) A flag to enable/disable public IP assigning on instances. `public_ips: false` requires `vpc_ids` that specifies custom networks with outbound internet connectivity provided by NAT Gateway or other mechanism. Defaults to `true`.  { #public_ips data-toc-label='public_ips' class='reference-item' }
###### `vm_managed_identity` - (Optional) The managed identity to associate with provisioned VMs. Must have a format `managedIdentityResourceGroup/managedIdentityName`.  { #vm_managed_identity data-toc-label='vm_managed_identity' class='reference-item' }
###### `tags` - (Optional) The tags that will be assigned to resources created by `dstack`.  { #tags data-toc-label='tags' class='reference-item' }
###### [`creds`](#azure-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=azure].creds` { #azure-creds data-toc-label="creds" }

=== "Client"
    ###### `type` -  The type of credentials. Must be `client`. { #type data-toc-label='type' class='reference-item' }
    ###### `client_id` -  The client ID.  { #client_id data-toc-label='client_id' class='reference-item' }
    ###### `client_secret` -  The client secret.  { #client_secret data-toc-label='client_secret' class='reference-item' }


=== "Default"
    ###### `type` -  The type of credentials. Must be `default`. { #type data-toc-label='type' class='reference-item' }


##### `projects[n].backends[type=gcp]` { #gcp data-toc-label="gcp" }

###### `type` -  The type of backend. Must be `gcp`. { #type data-toc-label='type' class='reference-item' }
###### `project_id` -  The project ID.  { #project_id data-toc-label='project_id' class='reference-item' }
###### `regions` - (Optional) The list of GCP regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### `vpc_name` - (Optional) The name of a custom VPC. If not specified, the default VPC is used.  { #vpc_name data-toc-label='vpc_name' class='reference-item' }
###### `extra_vpcs` - (Optional) The names of additional VPCs used for multi-NIC instances, such as those that support GPUDirect. Specify eight VPCs to maximize bandwidth in clusters with eight-GPU instances. Each VPC must have a subnet and a firewall rule allowing internal traffic across all subnets.  { #extra_vpcs data-toc-label='extra_vpcs' class='reference-item' }
###### `roce_vpcs` - (Optional) The names of additional VPCs with the RoCE network profile. Used for RDMA on GPU instances that support the MRDMA interface type. A VPC should have eight subnets to maximize the bandwidth in clusters with eight-GPU instances..  { #roce_vpcs data-toc-label='roce_vpcs' class='reference-item' }
###### `vpc_project_id` - (Optional) The shared VPC hosted project ID. Required for shared VPC only.  { #vpc_project_id data-toc-label='vpc_project_id' class='reference-item' }
###### `public_ips` - (Optional) A flag to enable/disable public IP assigning on instances. Defaults to `true`.  { #public_ips data-toc-label='public_ips' class='reference-item' }
###### `nat_check` - (Optional) A flag to enable/disable a check that Cloud NAT is configured for the VPC. This should be set to `false` when `public_ips: false` and outbound internet connectivity is provided by a mechanism other than Cloud NAT such as a third-party NAT appliance. Defaults to `true`.  { #nat_check data-toc-label='nat_check' class='reference-item' }
###### `vm_service_account` - (Optional) The service account to associate with provisioned VMs.  { #vm_service_account data-toc-label='vm_service_account' class='reference-item' }
###### `tags` - (Optional) The tags (labels) that will be assigned to resources created by `dstack`.  { #tags data-toc-label='tags' class='reference-item' }
###### `preview_features` - (Optional) The list of preview GCP features to enable. There are currently no preview features.  { #preview_features data-toc-label='preview_features' class='reference-item' }
###### [`creds`](#gcp-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=gcp].creds` { #gcp-creds data-toc-label="creds" }

=== "Service account"
    ###### `type` -  The type of credentials. Must be `service_account`. { #type data-toc-label='type' class='reference-item' }
    ###### `filename` -  The path to the service account file.  { #filename data-toc-label='filename' class='reference-item' }
    ###### `data` - (Optional) The contents of the service account file. When configuring via `server/config.yml`, it's automatically filled from `filename`. When configuring via UI, it has to be specified explicitly.  { #data data-toc-label='data' class='reference-item' }


    ??? info "Specifying `data`"
        To specify service account file contents as a string, use `jq`:

        ```shell
        cat my-service-account-file.json | jq -c | jq -R
        ```

=== "Default"




##### `projects[n].backends[type=lambda]` { #lambda data-toc-label="lambda" }

###### `type` -  The type of backend. Must be `lambda`. { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of Lambda regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#lambda-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=lambda].creds` { #lambda-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }


##### `projects[n].backends[type=nebius]` { #nebius data-toc-label="nebius" }

###### `type` -  The type of backend. Must be `nebius`. { #type data-toc-label='type' class='reference-item' }
###### `projects` - (Optional) The list of allowed Nebius project IDs. Omit to use the default project in each region. The project is considered default if it is the only project in the region or if its name starts with `default`.  { #projects data-toc-label='projects' class='reference-item' }
###### `regions` - (Optional) The list of allowed Nebius regions. Omit to allow all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### `fabrics` - (Optional) The list of allowed fabrics for InfiniBand clusters. Omit to allow all fabrics.  { #fabrics data-toc-label='fabrics' class='reference-item' }
###### `tags` - (Optional) The tags (labels) that will be assigned to resources created by `dstack`.  { #tags data-toc-label='tags' class='reference-item' }
###### `creds` -  The credentials.  { #creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=nebius].creds` { #nebius-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `service_account`. { #type data-toc-label='type' class='reference-item' }
###### `service_account_id` - (Optional) Service account ID. Set automatically if `filename` is specified. When configuring via the UI, it must be specified explicitly.  { #service_account_id data-toc-label='service_account_id' class='reference-item' }
###### `public_key_id` - (Optional) ID of the service account public key. Set automatically if `filename` is specified. When configuring via the UI, it must be specified explicitly.  { #public_key_id data-toc-label='public_key_id' class='reference-item' }
###### `private_key_file` - (Optional) Path to the service account private key. Set automatically if `filename` or `private_key_content` is specified. When configuring via the UI, it must be specified explicitly.  { #private_key_file data-toc-label='private_key_file' class='reference-item' }
###### `private_key_content` - (Optional) Content of the service account private key. When configuring via `server/config.yml`, it's automatically filled from `private_key_file`. When configuring via UI, it has to be specified explicitly.  { #private_key_content data-toc-label='private_key_content' class='reference-item' }
###### `filename` - (Optional) The path to the service account credentials file.  { #filename data-toc-label='filename' class='reference-item' }


##### `projects[n].backends[type=runpod]` { #runpod data-toc-label="runpod" }

###### `regions` - (Optional) The list of RunPod regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### `community_cloud` - (Optional) Whether Community Cloud offers can be suggested in addition to Secure Cloud. Defaults to `true`.  { #community_cloud data-toc-label='community_cloud' class='reference-item' }
###### [`creds`](#runpod-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=runpod].creds` { #runpod-creds data-toc-label="creds" }

###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }


##### `projects[n].backends[type=vastai]` { #vastai data-toc-label="vastai" }

###### `type` -  The type of backend. Must be `vastai`. { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of VastAI regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#vastai-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=vastai].creds` { #vastai-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }


<!--

##### `projects[n].backends[type=tensordock]` { #tensordock data-toc-label="tensordock" }

###### `type` -  The type of backend. Must be `tensordock`. { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of TensorDock regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#tensordock-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=tensordock].creds` { #tensordock-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }
###### `api_token` -  The API token.  { #api_token data-toc-label='api_token' class='reference-item' }


-->

##### `projects[n].backends[type=oci]` { #oci data-toc-label="oci" }

###### `type` -  The type of backend. Must be `oci`. { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of OCI regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### `compartment_id` - (Optional) Compartment where `dstack` will create all resources. Omit to instruct `dstack` to create a new compartment.  { #compartment_id data-toc-label='compartment_id' class='reference-item' }
###### [`creds`](#oci-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=oci].creds` { #oci-creds data-toc-label="creds" }

=== "Client"
    ###### `type` -  The type of credentials. Must be `client`. { #type data-toc-label='type' class='reference-item' }
    ###### `user` -  User OCID.  { #user data-toc-label='user' class='reference-item' }
    ###### `tenancy` -  Tenancy OCID.  { #tenancy data-toc-label='tenancy' class='reference-item' }
    ###### `key_file` - (Optional) Path to the user's private PEM key. Either this or `key_content` should be set.  { #key_file data-toc-label='key_file' class='reference-item' }
    ###### `key_content` - (Optional) Content of the user's private PEM key. Either this or `key_file` should be set.  { #key_content data-toc-label='key_content' class='reference-item' }
    ###### `pass_phrase` - (Optional) Passphrase for the private PEM key if it is encrypted.  { #pass_phrase data-toc-label='pass_phrase' class='reference-item' }
    ###### `fingerprint` -  User's public key fingerprint.  { #fingerprint data-toc-label='fingerprint' class='reference-item' }
    ###### `region` -  Name or key of any region the tenancy is subscribed to.  { #region data-toc-label='region' class='reference-item' }


=== "Default"
    ###### `type` -  The type of credentials. Must be `default`. { #type data-toc-label='type' class='reference-item' }
    ###### `file` - (Optional) Path to the OCI CLI-compatible config file. Defaults to `~/.oci/config`. { #file data-toc-label='file' class='reference-item' }
    ###### `profile` - (Optional) Profile to load from the config file. Defaults to `DEFAULT`. { #profile data-toc-label='profile' class='reference-item' }


##### `projects[n].backends[type=cudo]` { #cudo data-toc-label="cudo" }

###### `type` -  The type of backend. Must be `cudo`. { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of Cudo regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### `project_id` -  The project ID.  { #project_id data-toc-label='project_id' class='reference-item' }
###### [`creds`](#cudo-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=cudo].creds` { #cudo-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }


##### `projects[n].backends[type=verda]` { #verda data-toc-label="verda" }

###### `type` -  The type of backend.  { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of Verda regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#verda-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=verda].creds` { #verda-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `client_id` -  The client ID.  { #client_id data-toc-label='client_id' class='reference-item' }
###### `client_secret` -  The client secret.  { #client_secret data-toc-label='client_secret' class='reference-item' }


##### `projects[n].backends[type=kubernetes]` { #kubernetes data-toc-label="kubernetes" }

###### `type` -  The type of backend. Must be `kubernetes`. { #type data-toc-label='type' class='reference-item' }
###### [`proxy_jump`](#kubernetes-proxy_jump) - (Optional) The SSH proxy jump configuration.  { #_proxy_jump data-toc-label='proxy_jump' class='reference-item' }
###### `namespace` - (Optional) The namespace for resources managed by `dstack`. Defaults to `default`. { #namespace data-toc-label='namespace' class='reference-item' }
###### [`kubeconfig`](#kubernetes-kubeconfig) -  The kubeconfig configuration.  { #_kubeconfig data-toc-label='kubeconfig' class='reference-item' }


###### `projects[n].backends[type=kubernetes].kubeconfig` { #kubernetes-kubeconfig data-toc-label="kubeconfig" }

###### `filename` - (Optional) The path to the kubeconfig file.  { #filename data-toc-label='filename' class='reference-item' }
###### `data` - (Optional) The contents of the kubeconfig file. When configuring via `server/config.yml`, it's automatically filled from `filename`. When configuring via UI, it has to be specified explicitly.  { #data data-toc-label='data' class='reference-item' }


??? info "Specifying `data`"
    To specify kubeconfig contents directly via `data`, convert it to a string:

    ```shell
    yq -o=json ~/.kube/config | jq -c | jq -R
    ```

###### `projects[n].backends[type=kubernetes].proxy_jump` { #kubernetes-proxy_jump data-toc-label="proxy_jump" }

###### `hostname` - (Optional) The external IP address or hostname of any node.  { #hostname data-toc-label='hostname' class='reference-item' }
###### `port` - (Optional) Any port accessible outside of the cluster.  { #port data-toc-label='port' class='reference-item' }


##### `projects[n].backends[type=vultr]` { #vultr data-toc-label="vultr" }

###### `type` -  The type of backend. Must be `vultr`. { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of Vultr regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#vultr-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=vultr].creds` { #vultr-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }


##### `projects[n].backends[type=amddevcloud]` { #amddevcloud data-toc-label="amddevcloud" }

###### `type` -  The type of backend.  { #type data-toc-label='type' class='reference-item' }
###### `project_name` - (Optional) The name of the project.  { #project_name data-toc-label='project_name' class='reference-item' }
###### `regions` - (Optional) The list of regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#amddevcloud-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=amddevcloud].creds` { #amddevcloud-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }


##### `projects[n].backends[type=digitalocean]` { #digitalocean data-toc-label="digitalocean" }

###### `type` -  The type of backend.  { #type data-toc-label='type' class='reference-item' }
###### `project_name` - (Optional) The name of the project.  { #project_name data-toc-label='project_name' class='reference-item' }
###### `regions` - (Optional) The list of regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#digitalocean-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=digitalocean].creds` { #digitalocean-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }


##### `projects[n].backends[type=hotaisle]` { #hotaisle data-toc-label="hotaisle" }

###### `type` -  The type of backend. Must be `hotaisle`. { #type data-toc-label='type' class='reference-item' }
###### `team_handle` -  The Hot Aisle team handle.  { #team_handle data-toc-label='team_handle' class='reference-item' }
###### `regions` - (Optional) The list of Hot Aisle regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#hotaisle-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=hotaisle].creds` { #hotaisle-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The Hot Aisle API key.  { #api_key data-toc-label='api_key' class='reference-item' }


##### `projects[n].backends[type=cloudrift]` { #cloudrift data-toc-label="cloudrift" }

###### `type` -  The type of backend. Must be `cloudrift`. { #type data-toc-label='type' class='reference-item' }
###### `regions` - (Optional) The list of CloudRift regions. Omit to use all regions.  { #regions data-toc-label='regions' class='reference-item' }
###### [`creds`](#cloudrift-creds) -  The credentials.  { #_creds data-toc-label='creds' class='reference-item' }


###### `projects[n].backends[type=cloudrift].creds` { #cloudrift-creds data-toc-label="creds" }

###### `type` -  The type of credentials. Must be `api_key`. { #type data-toc-label='type' class='reference-item' }
###### `api_key` -  The API key.  { #api_key data-toc-label='api_key' class='reference-item' }


### `encryption` { #encryption data-toc-label="encryption" }

###### `keys` -  The encryption keys.  { #keys data-toc-label='keys' class='reference-item' }


#### `encryption.keys` { #encryption-keys data-toc-label="keys" }

##### `encryption.keys[n][type=identity]` { #encryption-keys-identity data-toc-label="identity" }

###### `type` -  The type of the key. Must be `identity`. { #type data-toc-label='type' class='reference-item' }


##### `encryption.keys[n][type=aes]` { #encryption-keys-aes data-toc-label="aes" }

###### `type` -  The type of the key. Must be `aes`. { #type data-toc-label='type' class='reference-item' }
###### `name` -  The key name for key identification.  { #name data-toc-label='name' class='reference-item' }
###### `secret` -  Base64-encoded AES-256 key.  { #secret data-toc-label='secret' class='reference-item' }


### `default_permissions` { #default_permissions data-toc-label="default_permissions" }

###### `allow_non_admins_create_projects` - (Optional) This flag controls whether regular users (non-global admins) can create and manage their own projects. Defaults to `True`. { #allow_non_admins_create_projects data-toc-label='allow_non_admins_create_projects' class='reference-item' }
###### `allow_non_admins_manage_ssh_fleets` - (Optional) This flag controls whether regular project members (i.e. Users) can add and delete SSH fleets. Defaults to `True`. { #allow_non_admins_manage_ssh_fleets data-toc-label='allow_non_admins_manage_ssh_fleets' class='reference-item' }

