# kn-migration plugin

Migrate Knative services from source cluster to destination cluster

## Plugin introduction

### Synopsis

Migrate Knative services from source cluster to destination cluster

```
kn migration --help
Migrate Knative services from source cluster to destination cluster

Usage:
  migration [command]

Available Commands:
  help        Help about any command
  list        List all knative resources
  migrate     Migrate Knative services from source cluster to destination cluster
```

### Examples

```
  # Migrate Knative services from source cluster to destination cluster by export KUBECONFIG and KUBECONFIG_DESTINATION as environment variables
  kn migration migrate --namespace default --destination-namespace default

  # Migrate Knative services from source cluster to destination cluster by set kubeconfig as parameters
  kn migration migrate --namespace default --destination-namespace default --kubeconfig $HOME/.kube/config/source-cluster-config.yml --destination-kubeconfig $HOME/.kube/config/destination-cluster-config.yml

  # Migrate Knative services from source cluster to destination cluster and force replace the service if exists in destination cluster
  kn migration migrate --namespace default --destination-namespace default --force

  # Migrate Knative services from source cluster to destination cluster and delete the service in source cluster
  kn migration migrate --namespace default --destination-namespace default --force --delete
```

### Options

```
      --delete                          Delete all Knative resources after kn-migration from source cluster
      --destination-kubeconfig string   The kubeconfig of the destination Knative resources (default is KUBECONFIG_DESTINATION from environment variable)
      --destination-namespace string    The namespace of the destination Knative resources
      --force                           Migrate service forcefully, replaces existing service if any.
  -h, --help                            help for migrate
  -n, --namespace string                The namespace of the source Knative resources (default "default")
```

### Options inherited from parent commands

```
      --config string       kn config file (default is $HOME/.kn/config.yaml)
      --kubeconfig string   kubectl config file (default is $HOME/.kube/config)
      --log-http            log http traffic
```

## Migration flow

### Step 1 Execute migrate command

![Step 1 Execute migrate command](docs/step1.png)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fknative-extensions%2Fkn-plugin-migration.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fknative-extensions%2Fkn-plugin-migration?ref=badge_shield)

### Step 2 Migrate first service with revisions

![Step 2 Migrate first service with revisions](docs/step2.png)

### Step 3 Migrate next service with revisions

![Step 3 Migrate next service with revisions](docs/step3.png)

### Step 4 Clean kn resources with --delete

![Step 4 Clean kn resources with --delete](docs/step4.png)


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fknative-extensions%2Fkn-plugin-migration.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fknative-extensions%2Fkn-plugin-migration?ref=badge_large)