## Installation

This assumes that you already have the 'identity' ready to go, and that your cluster is set up for persistent volume provisioning.

1. Make sure you have an appropriate storage driver for persistent volumes.
2. Install the helm chart, with a values.yaml that:
  - Has `setupMode: true` at the top level.
  - Exposes it via a LoadBalancer, Ingress, or other means of your choosing (it is ClusterIP by default).
  - If needed, customize values such as storage classes.
3. After it spins up, log into the file uploader with `admin:admin`.
4. Upload your identity files into the 'identity' directory.
5. If migrating an existing install, upload your master.db into the `config` directory. Do not upload any actual configuration files, as they may have incorrect paths.
6. Upgrade the helm chart, now with `setupMode: false` (the default).
7. After waiting for it to spin up, check that you can navigate to the dashboard.

You should end up with the following files uploaded that looks like this. The rest of the files will either be generated, or are part of the base image.

```
/app/
  config/
    master.db
  identity/
    multinode/
      ca.cert
      ca.key
      identity.cert
      identity.key
```

