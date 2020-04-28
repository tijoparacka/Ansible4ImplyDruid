Druid Ansible
===============

This project can setup a  imply  cluster

Preparations
----------------

Instances:
Create the instances where you would like to install druid. Installing zookeeper is not part of this scripts

Storage:

This script will create folder for the following . Currently deepstorage with local disk is supported.
- logs
- data
- deepstorage

User:


#ansible playbook variable configuration

in vars/druid.yml supply the needed  variables:

```
imply_version: 3.2.0
imply_download_url: https://static.imply.io/release/imply-{{ imply_version }}.tar.gz
druid_run_user: druid
zookeeper_url: localhost:2181

druid_environment: dev
druid_root_logger_level: info

druid_conf_dir: /opt/druid/conf
druid_base_dir: /opt/imply/
druid_tmpdir: /tmp
segment_cache_location: "{{ druid_base_dir }}/druid-data"
druid_extensions_dir: "{{ druid_base_dir}}/druid/extensions
druid_indexer_task_baseDir: "{{ druid_tmpdir }}/druid/task"
```

To execute the playbook,  execute the below command.

```ansible-playbook  -i inventories/development/cluster.ini  -u <user eg: centos> --private-key  <key file > cluster_setup.yml ```
