# nightscout

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square) ![AppVersion: 1.0.0](https://img.shields.io/badge/AppVersion-1.0.0-informational?style=flat-square)

nightscout helm package

**This chart is not maintained by the upstream project and any issues with the chart should be raised [here](https://github.com/k8s-at-home/charts/issues/new/choose)**

## Source Code

* <https://github.com/nightscout/nightscout-docker>

## Requirements

Kubernetes: `>=1.16.0-0`

## Dependencies

| Repository | Name | Version |
|------------|------|---------|
| https://library-charts.k8s-at-home.com | common | 4.0.0 |

## TL;DR

```console
helm repo add k8s-at-home https://k8s-at-home.com/charts/
helm repo update
helm install nightscout k8s-at-home/nightscout
```

## Installing the Chart

To install the chart with the release name `nightscout`

```console
helm install nightscout k8s-at-home/nightscout
```

## Uninstalling the Chart

To uninstall the `nightscout` deployment

```console
helm uninstall nightscout
```

The command removes all the Kubernetes components associated with the chart **including persistent volumes** and deletes the release.

## Configuration

Read through the [values.yaml](./values.yaml) file. It has several commented out suggested values.
Other values may be used from the [values.yaml](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common/values.yaml) from the [common library](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common).

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

```console
helm install nightscout \
  --set env.TZ="America/New York" \
    k8s-at-home/nightscout
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart.

```console
helm install nightscout k8s-at-home/nightscout -f values.yaml
```

## Custom configuration

N/A

## Values

**Important**: When deploying an application Helm chart you can add more values from our common library chart [here](https://github.com/k8s-at-home/library-charts/tree/main/charts/stable/common)
**Important**: Some of the below environment variables are **required** to be set for Nightscout to function.

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| env | object | See below | environment variables. See more environment variables in the [Nightscout documentation](https://github.com/nightscout/cgm-remote-monitor#environments). |
| env.TZ | string | `"UTC"` | Set the container timezone |
| env.MONGODB_URI | none | **REQUIRED**: MongoDB URI |
| env.API_SECRET | none | **REQUIRED**: API secret. Must be at least 12 characters long. |
| env.MONGODB_COLLECTION | `"entries"` | **REQUIRED**: MongoDB collection where entries are stored. |
| env.DISPLAY_UNITS | `"mg/dl"` | **REQUIRED**: Display units for BG values. Valid values are mg/dl or mmol |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy |
| image.repository | string | `"nightscout/nightscout"` | image repository |
| image.tag | string | chart.appVersion | image tag |
| ingress.main | object | See values.yaml | Enable and configure ingress settings for the chart under this key. |
| persistence | object | See values.yaml | Configure persistence settings for the chart under this key. |
| service | object | See values.yaml | Configures service settings for the chart. |

## Changelog

### Version 1.0.0

#### Added

- Initial version

#### Changed

N/A

#### Fixed

N/A

## Support

- See the [Docs](https://docs.k8s-at-home.com/our-helm-charts/getting-started/)
- Open an [issue](https://github.com/k8s-at-home/charts/issues/new/choose)
- Ask a [question](https://github.com/k8s-at-home/organization/discussions)
- Join our [Discord](https://discord.gg/sTMX7Vh) community

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)