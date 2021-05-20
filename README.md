# Mbtileserver helm chart

Helm 3 chart for [mbtileserver](https://github.com/consbio/mbtileserver)

## Install/Upgrade

First add the repo
```sh
helm repo add dax https://daxgrid.github.io/charts/
helm repo update
```

Install the chart
```sh
helm upgrade --install my-release-name dax/mbtileserver \
  --set storage.claimName=my-claim-name \
  --set 'commandArgs={-v, -d, /data}'
```

## Parameters
Parameters for the helm chart.

| Parameter              | Description                                | Default                  |
|------------------------|--------------------------------------------|--------------------------|
| `image.repository`     | The image for mbtileserver                 | `"consbio/mbtileserver"` |
| `image.tag`            | The tag for mbtileserver                   | `latest`                 |
| `storage.claimName`    | Name of the storage that should be mounted | `""`                     |
| `storage.path`         | Path where the storage should be mounted   | `/data`                  |
| `service.externalPort` | The external port                          | `80`                     |
| `service.type`         | The service type                           | `LoadBalancer`           |
| `commandArgs`          | Arguments mbtileserver is called with      | `{-v, -d, /data}`        |


helm upgrade --install my-release-name mbtileserver \
  --namespace=openftth \
  --set storage.claimName=openftth-tilegenerator-tippecanoe \
  --set 'commandArgs={--enable-reload-signal, -v, -d, /data}'
