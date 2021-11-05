# Policy Controller Audit Dashboard

Resources in this directory are used to create the log-based metric and dashboard to visualize the audit information from ACM Policy Controller (Also compatible with opensource OPA Gatekeeper).

These require that the cluster have application logging enabled, so that the logs will be available in Operations Suite (formerly Stackdriver).

## Dashboard Features

* Shows all audit events across all clusters in the project.
* Allows drill-down/filtering in the following dimensions:
  * Cluster Name
  * Constraint Name
  * Violating Resource Name
  * Violating Resource Namespace
* Includes charts for count visualization
* Includes a table with violating resource information, and current status

## Setup Instructions

1) Create the log based metric
```
gcloud logging metrics create policy_controller_violations_audited \
    --config-from-file=policy_controller_audit_log_metric.yaml
```

2) Create the dashboard
```
gcloud monitoring dashboards create \
    --config-from-file=policy_controller_audit_dashboard.json
```


