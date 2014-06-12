#aspects_elasticsearch

Install and configure the Elasticsearch database.

##Requirements

Set ```hash_behaviour=merge``` in your ansible.cfg file.

##Role Variables

###aspects_elasticsearch_install
Set as ```true``` to run installation tasks.
Set as ```false``` to skip installation tasks.

###aspects_elasticsearch_use_oracle_java
Set as ```'true``` if you want to use aspects_oracle_java to install oracle java.
Leave as ```false```, otherwise.

You will want to set as true if you are on a Suse system.

###aspects_elasticsearch_major_version_number
The version of elasticsearch to install. Defaults to: 1.1
See http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/setup-repositories.html for other options.

###aspects_elasticsearch_conf
Various options to set in /etc/elasticsearch/elasticsearch.yml

Currently supported:
* cluster_name: set ```cluster.name```, default: false
* data_path: set ```path.data```, default: false
* multicast_enabled: set ```discovery.zen.ping.multicast.enabled```, default: false
* unicast_hosts: set ```discovery.zen.ping.unicast.hosts```, default: false
* disable_allocation: set ```index.routing.allocation.disable_allocation```, default: undefined
* mlockall: set ```bootstrap.mlockall```, default: undefined

Note that ```node.name``` defaults to ```{{ ansible_hostname }}``` in the template file.

##Dependencies

* aspects_common_packages


Example Playbook
-------------------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: elasticsearch_servers
      roles:
         - { role: aspects_elasticsearch }
      vars:
        aspects_elasticsearch_conf:
          cluster_name: testing

License
-------

MIT