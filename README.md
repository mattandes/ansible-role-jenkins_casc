Ansible Role: Jenkins-CasC
=========

Configures the [Jenkins Configuration as Code plugin](https://plugins.jenkins.io/configuration-as-code-support) on a EL 7 system that was preferrably configured with the [geerlingguy.jenkins](https://galaxy.ansible.com/geerlingguy/jenkins) Ansible role. 

Requirements
------------

* Root access
* Jenkins Installed (Can be installed via geerlingguy.jenkins role)
* Configuration as Code Plugins installed (Can be installed via geerlingguy.jenkins)


Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

    jenkins_casc_config_file: "jenkins.yaml"

Tells the role the location of the JCasC config file to deploy to the Jenkins server. Defaults to the provided `jenkins.yaml` in the files directory of this role. This variable can also be set to a directory which will then copy all files in it to the server.

Dependencies
------------

The role expects a user named `jenkins` to be present on the system along with a service also named `jenkins` running that it can restart. Run the geerlingguy.jenkins role to take care of this for you.

Example Playbook
----------------

    - hosts: jenkins
      become: yes
      vars:
        java_packages:
          - java-1.8.0-openjdk
        jenkins_plugins:
          - configuration-as-code
          - configuration-as-code-support
      roles:
        - role: geerlingguy.java
        - role: geerlingguy.jenkins
        - role: mattandes.jenkins-casc

License
-------

MIT
