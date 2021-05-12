# Example Grafana Dashboards

There are a number of ways to load custom dashboards in Grafana. One way is through the Grafana GUI, but this is a manual process and may be cumbersome if you have to do it more than once. The process can be automated via the use of a Kubernetes [git-sync](https://github.com/kubernetes/git-sync) container running as a Grafana "sidecar" and a preconfigured Git repository containing custom Grafana dashboards. Follow the steps below to implement the automated approach:

To get started, create a [`new repository`](https://github.com/boozallen-software-studio/example-grafana-dashboards/generate) from this `example-grafana-dashboards` template. Then modify the Software Studio Platform [`variables.yaml`](https://github.com/boozallen-software-studio/platform/blob/master/src/main/terraform/variables.sample.yaml) file:
1. Set `prometheus-stack.grafana.custom_dashboards.repo` to the URL of the new repo.
2. Set `prometheus-stack.grafana.custom_dashboards.enabled` to `true`.

> **Note:** For a full list of configuration variables, see the documentation on [configuring custom dashboards for Grafana](https://pages.github.boozallencsn.com/uip/docs/platform/latest/components/prometheus-stack.html#_configuring_custom_dashboards_for_grafana).

Store your custom dashboards inside the [`dashboards`](./dashboards/) folder and the git-sync container will pick them up and add them to your list of dashboards viewable within Grafana.
