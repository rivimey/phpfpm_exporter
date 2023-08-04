Ansible Role: phpfpm\_exporter
==========================

Install and configure Prometheus phpfpm\_exporter.

Requirements
------------

An Ansible 2.2 or higher installation.<br />
This role makes use of the Ansible `json_filter` that requires `jmespath` to be installed on the Ansible machine.
See the `requirements.txt` file for further details on the specific version of `jmespath` required by the role.

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

    phpfpm_exporter_release_tag: "latest"

The phpfpm\_exporter release to be installed.
By default, the latest release published at https://github.com/hipages/php-fpm\_exporter/releases.

    phpfpm_exporter_release_url: ""

If set, the role will download phpfpm-exporter from the provided URL instead of using the download URL indicated in the phpfpm\_exporter Github release metadata.

    phpfpm_exporter_user: "phpfpm_exporter"
    phpfpm_exporter_group: "phpfpm_exporter"

phpfpm\_exporter system user and group.

    phpfpm_exporter_install_path: "/opt"

Directory containing the downloaded phpfpm\_exporter release artifacts.

    phpfpm_exporter_bin_path: "/usr/local/bin"

Directory to which the phpfpm\_exporter binaries will be symlinked.

    phpfpm_exporter_listen_address: "127.0.0.1:9100"

The phpfpm\_exporter WebServer listen ip address and port.<br/>
**NOTE**: the phpfpm\_exporter metrics will be available at `{{ phpfpm_exporter_listen_address }}/metrics`.

    phpfpm_exporter_log_level: "info"

phpfpm\_exporter logs verbosity level.

    phpfpm_exporter_additional_cli_args: ""

Additional command-line arguments to be added to the phpfpm\_exporter service unit.
For the complete refence of the available CLI arguments please refer to the output
of the `phpfpm_exporter --help` command.

Dependencies
------------

None.

Example Playbooks
-----------------

    $ cat playbook.yml
    - name: "Install and configure Prometheus phpfpm_exporter"
      hosts: all
      roles:
        - { role: rivimey.phpfpm_exporter }

Testing
-------

Tests are automated with [Molecule](http://molecule.readthedocs.org/en/latest/).

    $ pip install tox

To test all the scenarios run

    $ tox

To run a custom molecule command

    $ tox -e py27-ansible29 -- molecule test -s phpfpm_exporter-latest

License
-------

MIT

Author Information
------------------

Ruth Ivimey-Cook