# netmaker

![Version: 0.9.0](https://img.shields.io/badge/Version-0.9.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v0.20.3](https://img.shields.io/badge/AppVersion-v0.20.3-informational?style=flat-square)

A Helm chart to run HA Netmaker on Kubernetes

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| oci://registry-1.docker.io/bitnamicharts | postgresql | 12.9.0 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| baseDomain | string | `"example.com"` |  |
| dns.RWX.storageClassName | string | `""` |  |
| dns.enabled | bool | `false` | whether or not to deploy coredns |
| dns.existingClaim | string | `""` |  |
| dns.storageSize | string | `"128Mi"` |  |
| externalDatabase.database | string | `"netmaker"` | postgress db |
| externalDatabase.existingSecret | string | `""` |  |
| externalDatabase.host | string | `"external.postgres.url"` | postgres host |
| externalDatabase.password | string | `""` | postgres pass for netmaker user. ignored if existingSecret is set |
| externalDatabase.port | int | `5432` | postgres hosts port |
| externalDatabase.secretKeys.passwordKey | string | `""` |  |
| externalDatabase.type | string | `"postgresql"` |  |
| externalDatabase.username | string | `"netmaker"` | postgres username |
| fullnameOverride | string | `""` | override the full name for netmaker objects |
| image.pullPolicy | string | `"IfNotPresent"` | Pull Policy for images |
| image.repository | string | `"gravitl/netmaker"` | The image repo to pull Netmaker image from |
| ingress.annotations.base."kubernetes.io/ingress.allow-http" | string | `"false"` | annotation to generate ACME certs if available |
| ingress.annotations.nginx."nginx.ingress.kubernetes.io/rewrite-target" | string | `"/"` | destination addr for route |
| ingress.annotations.nginx."nginx.ingress.kubernetes.io/ssl-redirect" | string | `"true"` | Redirect http to https |
| ingress.annotations.rest | object | `{}` |  |
| ingress.annotations.tls."kubernetes.io/tls-acme" | string | `"true"` | use acme cert if available |
| ingress.annotations.traefik."traefik.ingress.kubernetes.io/redirect-entry-point" | string | `"https"` | Redirect to https |
| ingress.annotations.traefik."traefik.ingress.kubernetes.io/redirect-permanent" | string | `"true"` | Redirect to https permanently |
| ingress.annotations.traefik."traefik.ingress.kubernetes.io/rule-type" | string | `"PathPrefixStrip"` | rule type |
| ingress.annotations.ui | object | `{}` |  |
| ingress.className | string | `"nginx"` |  |
| ingress.enabled | bool | `true` | attempts to configure ingress if true |
| ingress.hostPrefix.rest | string | `"api."` | api (REST) route subdomain |
| ingress.hostPrefix.ui | string | `"dashboard."` | ui route subdomain |
| ingress.tls.enabled | bool | `false` |  |
| ingress.tls.issuerName | string | `"letsencrypt-prod"` |  |
| mq.endpoint | string | `"ws://netmaker-mqtt:1883"` |  |
| mq.existingSecret | string | `""` |  |
| mq.password | string | `"3yyerWGdds43yegGR"` |  |
| mq.secretKey | string | `""` |  |
| mq.username | string | `"netmaker"` |  |
| nameOverride | string | `""` | override the name for netmaker objects |
| oauth.enabled | bool | `false` |  |
| oauth.existingSecret | string | `""` |  |
| oauth.provider | string | `"oidc"` |  |
| oauth.secretKeys.clientID | string | `nil` |  |
| oauth.secretKeys.clientSecret | string | `nil` |  |
| oauth.secretKeys.frontendURL | string | `nil` |  |
| oauth.secretKeys.issuer | string | `nil` |  |
| persistence.sharedData.existingClaim | string | `""` |  |
| podAnnotations | object | `{}` | pod annotations to add |
| podSecurityContext | object | `{}` | pod security contect to add |
| postgresql.auth.database | string | `"netmaker"` |  |
| postgresql.auth.existingSecret | string | `""` |  |
| postgresql.auth.password | string | `""` |  |
| postgresql.auth.secretKeys.adminPasswordKey | string | `""` |  |
| postgresql.auth.secretKeys.userPasswordKey | string | `""` |  |
| postgresql.auth.username | string | `"netmaker"` |  |
| postgresql.enabled | bool | `true` |  |
| postgresql.persistence.existingClaim | string | `""` |  |
| replicas | int | `1` | number of netmaker server replicas to create |
| service.restPort | int | `8081` | port for API service |
| service.type | string | `"ClusterIP"` | type for netmaker server services |
| service.uiPort | int | `80` | port for UI service |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | Name of SA to use. If not set and create is true, a name is generated using the fullname template |
| setIpForwarding.enabled | bool | `true` |  |
| ui.replicas | int | `1` | how many UI replicas to create |
| wireguard.enabled | bool | `true` | whether or not to use WireGuard on server |
| wireguard.kernel | bool | `false` | whether or not to use Kernel WG (should be false unless WireGuard is installed on hosts). |
| wireguard.networkLimit | int | `10` | max number of networks that Netmaker will support if running with WireGuard enabled |
| wireguard.service.annotations | object | `{}` |  |
| wireguard.service.serviceType | string | `"NodePort"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
