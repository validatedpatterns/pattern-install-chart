# pattern-install

![Version: 0.0.2](https://img.shields.io/badge/Version-0.0.2-informational?style=flat-square)

A Helm chart to build and deploy a Cloud Pattern via the patterns operator

This chart is used by the Validated Patterns installation script that can be found [here](https://github.com/validatedpatterns/common/blob/main/scripts/pattern-util.sh)

**Homepage:** <https://github.com/validatedpatterns/pattern-install-chart>

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Validated Patterns Team | <validatedpatterns@googlegroups.com> |  |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.extraValueFiles | list | `[]` | List of additional value files to be passed to the pattern |
| main | object | depends on the individual settings | main is used primarly for initial bootstrap pattern configuration |
| main.clusterGroupName | string | `"default"` | Name of the clusterGroup to be used. Drives the clusterGroup chart |
| main.experimentalCapabilities | string | `""` | String to enable certain experimental capabilities in the operator and the framework. Not needed unless you know exactly what you're doing. |
| main.git | object | depends on the individual settings | Settings related to the Git repository used to deploy the pattern |
| main.git.repoURL | string | `"https://github.com/pattern-clone/mypattern"` | Repository URL pointing to the pattern |
| main.git.repoUpstreamURL | string | `nil` | Setting this field will make it so that an in-cluster gitea instance will be spawned. `repoURL` will be ignored and the pattern will be deployed using the in-gitea URL |
| main.git.revision | string | `"main"` | The branch or Git reference to use to deploy the pattern |
| main.gitops | object | depends on the individual settings | Settings related to the gitops operator |
| main.gitops.channel | string | `"gitops-1.13"` | Default channel to install the gitops operator from |
| main.gitops.operatorSource | string | `"redhat-operators"` | Source to be used to install the gitops operator from |
| main.multiSourceConfig.clusterGroupChartVersion | string | `nil` | The clustergroup chart version to be used when deploying a pattern (defaults to 0.8.*) |
| main.multiSourceConfig.enabled | bool | `false` | Enables a multisource configuration for the clustergroup chart |
| main.multiSourceConfig.helmRepoUrl | string | `nil` | The URL of the VP helm charts repository (defaults to https://charts.validatedpatterns.io) |
| main.patternsOperator | object | depends on the individual settings | Settings related to the patterns operator installation |
| main.patternsOperator.channel | string | `"fast"` | channel name to install the patterns operator from |
| main.patternsOperator.installPlanApproval | string | `"Automatic"` | Installation plan approval of the patterns operator |
| main.patternsOperator.source | string | `"community-operators"` | Source to be used to install the patterns operator from |
| main.patternsOperator.sourceNamespace | string | `"openshift-marketplace"` | Source namespace to install the patterns operator from |
| main.patternsOperator.startingCSV | string | `nil` | Starting CSV for the install of the patterns operator |
| main.tokenSecret | string | `nil` | Name of the secret containing access credentials to clone the Git repository to deploy the pattern See https://validatedpatterns.io/blog/2023-12-20-private-repos/ for more information |
| main.tokenSecretNamespace | string | `nil` | Namespace where the above secret will be |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)

## Update CRD

In order to update the CRD, copy the following file from the last released
patterns operator version:

```sh
cp -v patterns-operator/config/crd/bases/gitops.hybrid-cloud-patterns.io_patterns.yaml ./crds/
```

