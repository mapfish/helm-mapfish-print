# HELM Mapfish Print

This repository provide an example values file that can be used with [helm-application](https://github.com/camptocamp/helm-application) to deploy a Mapfish Print service.

With the following values, you will have a print with:

- Use a database to make the cluster mode working.
- Mask the metrics views [TODO].
- Expose the JMX metrics to Prometheus.
- Configure a PodDisruptionBudget.
- Configure an Ingress.

To expose the JMX metrics to Prometheus, we:

- Get the `jmx_prometheus_javaagent.jar` from the `bitnami/jmx-exporter` image.
- Create a `jmx-exporter.yaml` configuration in a ConfigMap.
- Run java with a `-javaagent:...` argument.
- Configure a `prometheus` port.
- Create a PodMonitor object to indicate to the Prometheus operator where he should get the metrics.
