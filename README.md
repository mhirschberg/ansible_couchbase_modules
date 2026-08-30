# Ansible modules for Couchbase

Custom Python-based Ansible modules for automating the lifecycle and security configuration of Couchbase clusters.

This project was developed for production infrastructure automation and maintained between 2018 and 2022. It uses the Ansible module layout of that period and is published as a portfolio and reference project rather than as a currently supported collection.

## Capabilities

| Module | Purpose |
| --- | --- |
| `couchbase_cluster` | Initialize clusters and manage memory, compaction, failover, and cluster settings |
| `couchbase_node` | Join nodes to clusters and move them between server groups |
| `couchbase_bucket` | Create Couchbase and Ephemeral buckets and update bucket settings |
| `couchbase_rbac` | Create and remove local or external users and manage roles and groups |
| `couchbase_security` | Configure LDAP, auditing, TLS restrictions, cipher suites, UI access, and session settings |

Shared discovery and cluster-state logic is implemented in `module_utils/couchbase_common.py`.

## Engineering focus

- Repeatable cluster deployment and lifecycle management
- State-aware infrastructure automation
- REST API and command-line integration
- RBAC and external identity integration
- Audit, TLS, and platform-hardening controls
- Operational handling of clustered and distributed systems

## Compatibility

- Ansible 2.4 or later in the legacy module layout
- Python `requests`
- Couchbase Server 6.6 or later
- Couchbase Server binaries installed on the managed nodes

The code has not been modernized into an Ansible Collection and should be reviewed before use with current Ansible or Couchbase releases.

## Installation

Place the modules in a directory included in `ANSIBLE_LIBRARY`, or alongside a playbook in `./library`. Place `couchbase_common.py` in the corresponding `module_utils` directory.

## Notes

- The full list of cluster nodes is required for reliable orchestrator detection.
- Check mode is not available for every security and failover operation.
- See the embedded module documentation for parameters and examples.

## Related projects

- [Couchbase rolling-upgrade playbook](https://github.com/mhirschberg/ansible_couchbase_playbooks)
- [Supporting Ansible roles](https://github.com/mhirschberg/ansible_roles)

Licensed under GPL-3.0.
