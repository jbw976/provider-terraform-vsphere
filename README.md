# provider-terraform-vsphere


## Overview

`provider-terraform-vsphere` is an experimental Crossplane infrastructure provider for
the vSphere [vCenter Server](https://www.vmware.com/products/vcenter-server.html) and
[ESXi](https://www.vmware.com/products/esxi-and-esx.html) APIs.
Available resources and their fields can be found in the [CRD
Docs](https://doc.crds.dev/github.com/crossplane-contrib/provider-terraform-vsphere).
Documentation for the original Terraform resources that were used to generate these CRDs,
and descriptions for the attributes which compose them, can be found in the documentation for the
[Terraform vSphere provider](https://registry.terraform.io/providers/hashicorp/vsphere/latest/docs).
Source code for the Terraform provider can be found at https://github.com/hashicorp/terraform-provider-vsphere
If you encounter an issue please reach out on
[slack.crossplane.io](https://slack.crossplane.io) and create an issue in
the [crossplane-contrib/provider-terraform-vsphere](https://github.com/crossplane-contrib/provider-terraform-vsphere)
repo.

* Custom Resource Definitions (CRDs) that model vSphere the infrastructure and services, following
  the schema observed in the Terraform vSphere Provider.
* Generated code enabling Go representations of the CRDs to be encoded and decoded to/from the native Terraform
  format [zclconf/go-cty](https://github.com/zclconf/go-cty) for serialization to the Terraform GRPC wire format
* Generated code enabling Go representations of Resources to be compared, so that differences between the desired
  and observed state of a Resource can be detected.
* Taken together, these capabilities enable the generic controller implemented in 
  [crossplane-contrib/terraform-runtime](https://github.com/crossplane-contrib/terraform-runtime) to fulfill the
  [crossplane/crossplane-runtime](https://github.com/crossplane/crossplane-runtime) `ExternalClient` interface.

This provider was generated by running https://github.com/crossplane-contrib/terraform-provider-gen
pointed at the plugin binary built from https://github.com/hashicorp/terraform-provider-vsphere

The same provider binary used to build the provider must also be present at runtime. Point the runtime at the
full path to the plugin on the local filesystem using the `--pluginPath=` cli flag. When using an official image
the appropriate plugin binary will be bundled. For local development, the binary required by `terraform-provider-gen.yaml`
can be downloaded using the command:
`go run github.com/crossplane-contrib/terraform-provider-dl --config=terraform-provider-gen.yaml --output=$DIRECTORY`

Where `$DIRECTORY` is the directory you would like to use for the `--pluginPath` argument. Please use an empty directory
because the plugin expects the directory to only contain the terraform  plugin.


## Demo

This is the demo we ran on the TBS livestream @ https://www.youtube.com/watch?v=nDZdQxjGAkw

```
./hack/integration-test/setup.sh
./demo.sh
kubectl apply -f examples/controller-config.yaml
kubectl apply -f examples/provider.yaml
kubectl apply -f hack/integration-test/provider
kubectl apply -f hack/integration-test/resources
```

## Getting Started and Documentation

For getting started guides, installation, deployment, and administration, see
our [Documentation](https://crossplane.io/docs/latest).

## Contributing

provider-terraform-vsphere is a community driven project and we welcome contributions. See the
Crossplane
[Contributing](https://github.com/crossplane/crossplane/blob/master/CONTRIBUTING.md)
guidelines to get started.

### Adding New Resource

Please see the documentation for [crossplane-contrib/terraform-provider-gen](https://github.com/crossplane-contrib/terraform-provider-gen)
for the latest documentation on using the code generation tools. This tool is still highly experimental so it is possible that new
resources could uncover edge cases that require further development on the shared codegen tools.

## Report a Bug

For filing bugs, suggesting improvements, or requesting new features, please
open an [issue](https://github.com/crossplane-contrib/provider-terraform-vsphere/issues).

## Contact

Please use the following to reach members of the community:

* Slack: Join our [slack channel](https://slack.crossplane.io)
* Forums:
  [crossplane-dev](https://groups.google.com/forum/#!forum/crossplane-dev)
* Twitter: [@crossplane_io](https://twitter.com/crossplane_io)
* Email: [info@crossplane.io](mailto:info@crossplane.io)

## Roadmap

provider-terraform-vsphere goals and milestones are currently tracked in the Crossplane
repository. More information can be found in
[ROADMAP.md](https://github.com/crossplane/crossplane/blob/master/ROADMAP.md).

## Governance and Owners

provider-aws is run according to the same
[Governance](https://github.com/crossplane/crossplane/blob/master/GOVERNANCE.md)
and [Ownership](https://github.com/crossplane/crossplane/blob/master/OWNERS.md)
structure as the core Crossplane project.

## Code of Conduct

provider-aws adheres to the same [Code of
Conduct](https://github.com/crossplane/crossplane/blob/master/CODE_OF_CONDUCT.md)
as the core Crossplane project.

## Licensing

provider-terraform-vsphere is licensed under the Apache License, Version 2.0.

[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fcrossplane-contrib%2Fprovider-terraform-vsphere.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fcrossplane-contrib%2Fprovider-terraform-vsphere?ref=badge_large)
