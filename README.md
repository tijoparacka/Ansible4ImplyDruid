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

Limitations:

We are in the process of improving the playbook . As of now following limitations applied.

1. Only one master is allowed to create
2. Supported only derby db in embedded mode
3. Zookeeper need to be installed separately; use the link to install zookeeper https://github.com/tijoparacka/zookeeper-cluster-ansible
4. Secure installation not done
5. S3 or any other cloud deep storage is  not done
6. Recommended configs based on the hardware is not done.
7. All the cluster restart scenarios are not tested
