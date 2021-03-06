# cf-deployment Experimental Ops-files

This is the README for Experimental Ops-files. To learn more about `cf-deployment`, go to the main [README](../README.md). 

- For general Ops-files, check out the [Ops-file README](../README.md).
- For Legacy Ops-files, check out the [Legacy Ops-file README](../legacy/README.md).
- For Community Ops-files, checkout the [Community Ops-file README](../community/README.md).

"Experimental" ops-files represent configurations
that we expect to promote to blessed configuration eventually,
meaning that,
once the configurations have been sufficiently validated,
they will become part of cf-deployment.yml
and the ops-files will be removed.

| Name | Purpose | Notes |
|:---  |:---     |:---   |
| [`bits-service.yml`](bits-service.yml) | Adds the [bits-service](https://github.com/cloudfoundry-incubator/bits-service) job and enables it in the cloud-controller. | Also requires one of `bits-service-{local,webdav,s3}.yml` from the same directory. |
| [`bits-service-local.yml`](bits-service-local.yml) | Use local storage for the [bits-service](https://github.com/cloudfoundry-incubator/bits-service). | |
| [`bits-service-s3.yml`](bits-service-s3.yml) | Use s3 storage for the [bits-service](https://github.com/cloudfoundry-incubator/bits-service). | `use-s3-blobstore.yml` from the root `operations` directory is also required. |
| [`bits-service-webdav.yml`](bits-service-webdav.yml) | Use the `blobstore`'s webdav storage for the [bits-service](https://github.com/cloudfoundry-incubator/bits-service). | Requires the `blobstore` job. |
| [`deploy-bosh-backup-restore.yml`](deploy-bosh-backup-restore.yml) | Deploy BOSH backup and restore instance. | |
| [`disable-consul-service-registrations-locket.yml`](disable-consul-service-registrations-locket.yml) | Prevents the `locket` server from registering itself as a service with Consul | Requires `enable-locket.yml` |
| [`disable-consul-service-registrations-windows.yml`](disable-consul-service-registrations-windows.yml) | Prevents the Windows Cell `rep` from registering itself as a service with Consul | Requires `enable-locket.yml` and `windows-cell.yml` |
| [`disable-consul-service-registrations.yml`](disable-consul-service-registrations.yml) | Prevents the `auctioneer`, `ssh_proxy`, `file_server`, `rep`, and `bbs` jobs from registering as a service with Consul | Requires `enable-locket.yml` |
| [`disable-etcd.yml`](disable-etcd.yml) | Removes the `etcd` instance group and disables `loggregator` components from using it. | |
| [`enable-container-proxy.yml`](enable-container-proxy.yml) | Enables container proxy on the Diego Cell `rep`. | |
| [`enable-instance-identity-credentials.yml`](enable-instance-identity-credentials.yml) | Enables identity credentials on Diego Cell `rep`. | |
| [`enable-iptables-logger.yml`](enable-iptables-logger.yml) | Enables iptables logger. | |
| [`enable-locket-postgres.yml`](enable-locket-postgres.yml) | Enables locket for diego-api when using the postgres database. | Requires `enable-locket.yml` and `enable-postgres.yml`, in that order. |
| [`enable-locket-windows.yml`](enable-locket-windows.yml) | Enable locket for the windows 2012 cell. | |
| [`enable-locket-windows2016.yml`](enable-locket-windows2016.yml) | Enable locket for the windows 2016 cell. | |
| [`enable-locket.yml`](enable-locket.yml) | Enables locket. | Assumes MySQL. To use with postgres, see `enable-locket-postgres.yml` |
| [`enable-loggregator-v2-diego.yml`](enable-loggregator-v2-diego.yml) | Intentionally left blank for backwards compatibility.  | Previously: "Use `v2` loggregator api for doppler communication." `cf-deployment.yml` now does this by default. |
| [`enable-loggregator-v2-windows-cell.yml`](enable-loggregator-v2-windows-cell.yml) |  Intentionally left blank for backwards compatibility. | Previously: "Use `v2` loggregator api for doppler communication from windows 2012 cells." `cf-deployment.yml` now does this by default. |
| [`enable-loggregator-v2-windows2016-cell.yml`](enable-loggregator-v2-windows2016-cell.yml) |  Intentionally left blank for backwards compatibility. | Previously: "Use `v2` loggregator api for doppler communication from windows 2016 cells." `cf-deployment.yml` now does this by default. |
| [`enable-prefer-declarative-healthchecks.yml`](enable-prefer-declarative-healthchecks.yml) | Configure the Rep on the diego cells to prefer LRP CheckDefinition (a.k.a declarative healthchecks) over the old Monitor action | |
| [`enable-prefer-declarative-healthchecks-windows.yml`](enable-prefer-declarative-healthchecks-windows.yml) | Configure the Rep on the windows 2012 cells to prefer LRP CheckDefinition (a.k.a declarative healthchecks) over the old Monitor action | |
| [`enable-prefer-declarative-healthchecks-windows2016.yml`](enable-prefer-declarative-healthchecks-windows2016.yml) | Configure the Rep on the windows 2016 cells to prefer LRP CheckDefinition (a.k.a declarative healthchecks) over the old Monitor action | |
| [`locket-postgres.yml`](locket-postgres.yml) | Symlink to `enable-locket-postgres.yml` for backwards compatibility. | |
| [`locket-windows.yml`](locket-windows.yml) | Symlink to `enable-locket-windows.yml` for backwards compatibility. | |
| [`locket.yml`](locket.yml) | Symlink to `enable-locket.yml` for backwards compatibility. | |
| [`secure-service-credentials.yml`](secure-service-credentials.yml) | Use CredHub for service credentials. | |
| [`skip-consul-cell-registrations.yml`](skip-consul-cell-registrations.yml) | Configure the BBS to only use locket to find cells in the deployment | Requires `enable-locket.yml` |
| [`skip-consul-locks.yml`](skip-consul-locks.yml) | Don't use consul locks in several jobs. | Requires `use-locket.yml`. |
| [`use-cf-networking-postgres.yml`](use-cf-networking-postgres.yml) | Intentionally left blank for backwards compatibility. |Previously: "Allows use of `use-cf-networking.yml` with the postgres database." `cf-deployment.yml` plus `use-postges.yml` now does this by default.
| [`use-cf-networking.yml`](use-cf-networking.yml) | Enable container-to-container networking features with cf-networking-release. | Assumes MySQL. To use with postgres, see `use-cf-networking-postgres.yml`. |
| [`use-external-cf-networking-dbs.yml`](use-external-cf-networking-dbs.yml) | Intentionally left blank for backwards compatibility. | Previously: "Allowed `user-cf-networking.yml` to work with external database." `cf-deployment.yml` plus `use-external-dbs.yml` now does this by default.
| [`use-external-locket-db.yml`](use-external-locket-db.yml) | Allows `enable-locket.yml` to work with external database. | Requires `enable-locket.yml` |
| [`use-grootfs.yml`](use-grootfs.yml) | Enable grootfs on diego cells. | |
| [`windows2016-cell.yml`](windows2016-cell.yml) | Deploys a windows 2016 diego cell, adds releases necessary for windows. |  |
