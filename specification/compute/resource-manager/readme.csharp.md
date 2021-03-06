# C# Compute

> see https://aka.ms/autorest

This is the AutoRest configuration file for DNS.

These settings apply only when `--csharp` is specified on the command line.
Please also specify `--csharp-sdks-folder=<path to "SDKs" directory of your azure-sdk-for-net clone>`.

## Common C# settings

``` yaml $(csharp)
csharp:
  azure-arm: true
  license-header: MICROSOFT_MIT_NO_VERSION
  payload-flattening-threshold: 1
  clear-output-folder: true
```

``` yaml $(csharp) && !$(multiapi) && !$(profile)
namespace: Microsoft.Azure.Management.Compute
output-folder: $(csharp-sdks-folder)/Compute/Management.Compute/Generated
```

## Batch settings
These settings are for batch mode only: (ie, add `--multiapi` to the command line )

```yaml $(multiapi)
namespace: Microsoft.Azure.Management.Compute.$(ApiVersionName)
output-folder: $(csharp-sdks-folder)/$(ApiVersionName)/Generated

batch:
  - tag: package-2017-03
    ApiVersionName: Api2017_03_30

  - tag: package-2016-03
    ApiVersionName: Api2016_03_30
```

```yaml $(profile)=='hybrid_2018_03_01'
namespace: Microsoft.Azure.Management.Profiles.$(profile).Compute
output-folder: $(csharp-sdks-folder)/$(profile)/Compute/Management.Compute/Generated
batch:
  - tag: package-disks-2018-04
  - tag: package-compute-only-2017-12
  - tag: package-skus-2017-09
  - tag: package-compute-2017-03
```

``` yaml $(profile)=='profile_2017_03_09'
namespace: Microsoft.Azure.Management.Profiles.$(profile).Compute
output-folder: $(csharp-sdks-folder)/$(profile)/Compute/Management.Compute/Generated

batch:
 - tag: package-compute-2016-03
 ```
