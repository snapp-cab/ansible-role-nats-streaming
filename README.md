# NATS Streaming Ansible Role

![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/snapp-cab/ansible-role-nats-streaming/ci.yaml?style=for-the-badge&logo=github)

NATS Streaming is a data streaming system powered by NATS, and written in the Go programming language.

## Installation

```yaml
# requirments.yaml
- src: git@github.com:snapp-incubator/ansible-role-nats-streaming.git
  scm: git
  version: master
  name: nats-streaming
```

## Role Variables

```yaml
nats_streaming_version: "0.18.0"
nats_streaming_host_group: "streaming"

nats_streaming_cluster_id: snapp
nats_streaming_nats_server_url: "nats.service.consul"

nats_streaming_store_limits_max_channels: 100
nats_streaming_store_limits_max_subs: 200
nats_streaming_store_limits_max_age: "48h"
nats_streaming_store_limits_max_inactivity: "72h"

nats_streaming_file_options_buffer_size: 16MB
nats_streaming_file_options_parallel_recovery: 4
nats_streaming_file_options_read_buffer_size: 16MB
nats_streaming_file_options_auto_sync: "1m"

nats_streaming_cluster_node_id: "{{ ansible_hostname }}"
nats_streaming_cluster_bootstrap: true
nats_streaming_cluster_log_cache_size: 4096
nats_streaming_cluster_sync: true

nats_exporter_enabled: "true"
nats_prometheus_exporter_version: "0.6.2"
```

## Example Playbook

```yaml
- hosts: some_servers
  vars:
    nats_streaming_version: "0.18.0"
    nats_streaming_host_group: "some_servers"
    nats_exporter_enabled: "true"
    nats_prometheus_exporter_version: "0.6.2"
  roles:
    - nats-streaming
```
