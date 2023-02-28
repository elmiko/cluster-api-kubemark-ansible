# cluster-api-kubemark-ansible

For setting up hosts with cluster-api and kubemark provider development
environment. Including tools to build source code, docker, and kind.

## Setting up a development host

1. Create an instance, ubuntu 22.04 is recommended
2. Update `inventory/hosts` if you need to change addresses
3. Run `ansible-playbook -K -i inventory setup_devel_environment.yaml`

Once it is finished you will be able to login to the host as the devel user
listed in the hosts file. All the development tools should be ready for access.

### Adding Tilt to a development environment

The Cluster API project has [good support][capitilt]
for [Tilt](https://tilt.dev/). It can be easily added to a devel system.

1. Modify `files/tilt-settings.yaml` as needed
2. Run `ansible-playing -K -i inventory add_tilt_to_devel_env.yaml`

Once installed you can start using Tilt by following the
[Cluster API instructions][capitilt].

## Building binaries and images

This will build the `clusterctl` binary and all the controller images, it will
also push the images to the local registry.

1. Complete previous step
2. Run `ansible-playbook -i inventory build_clusterctl_and_images.yaml`

[capitilt]: https://cluster-api.sigs.k8s.io/developer/tilt.html
