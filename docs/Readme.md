<p align="center"><img src="./img/lo.svg" width="260"></p>
<p align="center">


# Logging Operator Documentation

### Welcome to the Logging Operator documentation!

There are a lot of things a user of Logging Operator might need to know about. To help you manage this logging information, we've divided the operator docs into several sections.



Logging-operator is a core part of the [Pipeline](https://beta.banzaicloud.io) platform, a Cloud Native application and devops platform that natively supports multi- and hybrid-cloud deployments with multiple authentication backends. Check out the developer beta:
 <p align="center">
   <a href="https://beta.banzaicloud.io">
   <img src="https://camo.githubusercontent.com/a487fb3128bcd1ef9fc1bf97ead8d6d6a442049a/68747470733a2f2f62616e7a6169636c6f75642e636f6d2f696d672f7472795f706970656c696e655f627574746f6e2e737667">
   </a>
 </p>


## Contents
- **[Installation](./deploy/README.md)**
  - [Deploy with Helm](./deploy/README.md#deploy-logging-operator-with-helm)
  - [Deploy with Kubernetes Manifests](./deploy/README.md#deploy-logging-operator-from-kubernetes-manifests)
- **[Supported Plugins](./plugins/Readme.md)**
- **[Examples](./docs)**
  - [S3 Output](./example-s3.md)
  - [Elasticsearch Output](./example-es-nginx.md)
  - [Loki Output](./example-loki-nginx.md)
  - [Kafka Output](./example-kafka-nginx.md)
  - [Amazon CloudWatch Output](./example-cloudwatch-nginx.md)
  - [And more...](./examples)
- **[Custom Resource Definitions](./crds.md)**
- **[Fluentbit Configuration](./fluentbit.md)**
- **[For Developers](./developers.md)**
- **[Monitoring](./logging-operator-monitoring.md)**
- **[Security](./security/README.md)**
- **[Requirements](#requirements)**
- **[Troubleshooting](./troubleshooting.md)**
- **[Contributing](../README.md#contributing)**
- **[Blogs](#blogs)**
- **[Licence](../LICENSE)**
---

## Requirements
 `Software`
 - Logging Operator requires use of Kubernetes v1.14.x and up.
 - For the [Helm base installation](./deploy/README.md#deploy-logging-operator-with-helm) we required Helm v2.16.0 or higher.
 
 `CPU and Memory`<br>
Hardware requirements scale based on the size of your cluster.<br>
Default configuration is:<br>
**Fluentbit:**
- Limits:
  - cpu: 200m
  - memory: 100M
- Requests:
  - cpu: 100m
  - memory: 50M

**FluentD**
- Limits:
  - cpu: 1
  - memory: 200M
- Requests:
  - cpu: 500m
  - memory:  100M

You can easily change this  
 ```yaml
apiVersion: logging.banzaicloud.io/v1beta1
kind: Logging
metadata:
  name: default-logging
  namespace: logging
spec:
  fluentd:
    resources:
      requests:
        cpu: 1
        memory: 1Gi
      limits:
        cpu: 2
        memory: 2Gi
  fluentbit: {}
    resources:
      requests:
        cpu: 500m
        memory: 500M
      limits:
        cpu: 1
        memory: 1Gi
```

 
## Blogs
  - [Logging-Operator v2](https://banzaicloud.com/blog/logging-operator-v2/)
  - [Eleasticsearch and GeoIP](https://banzaicloud.com/blog/logging-operator-efk/)  

##### Blogs (general logging and operator v1)
  - [Advanced logging on Kubernetes](https://banzaicloud.com/blog/k8s-logging-advanced/)
  - [Secure logging on Kubernetes with Fluentd and Fluent Bit](https://banzaicloud.com/blog/k8s-logging-tls/)
  - [Centralized logging under Kubernetes](https://banzaicloud.com/blog/k8s-logging/)
  - [Centralized logging on Kubernetes automated](https://banzaicloud.com/blog/k8s-logging-operator/)
  - [And more...](https://banzaicloud.com/tags/logging/)
