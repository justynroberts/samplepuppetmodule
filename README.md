Supplied as is and based on blueprint from on https://github.com/instana/instana-agent-puppet


`` ``
# Table of contents
`` ``
# Deploy instana on a Host


`` yaml
environment: preproduction
parameters:
  factory: yes
  application: Myapp
`` ``

Then start an puppet agent, with the possibility of using the _instana_agent_ tag:
`` bash
sudo puppet agent -t --tags instana_agent
``



## Personalization

In order to allow improved customization, a module system has been set up and allows  addition of configuration on specific technologies:
* statsd
* repeat
* php
* memcached
* javatrace

This list can be extended by adding the necessary classes to the puppet module. This customization is based on the way the instana agent loads its configurations.
[Reference] (https://docs.instana.io/quick_start/agent_configuration/#configuration)

The configuration files for the different modules must be generated in the form `configuration-techno.yaml` and will be loaded in system order (generally ascii / alphabetical order). Keep in mind that the latest files overload the previous ones.

### Using an already existing technology

To activate a module you must have at least for example (for the statsd technology):

`` yaml
  instana_agent :: modules :: statsd:
    enabled: true
``
Depending on the different technologies, one or more additional parameters could be mandatory or available, please read the part specific to your techno before use that you will find below.

In order to combine ease and allow customization, a level of templates has been set up, you will have at your disposal a default template to quickly use the functionality. But you will also be able to extend the functionalities by using templates by factory, by machine or by application.



#### Technologies available

For each of the available technologies, the so-called complete configuration refers to the most complete configuration proposed by the puppet module, it could be incomplete or evolve, it is for this reason that the link to the official documentation is proposed.

The complete configuration therefore corresponds to the configuration that will have been proposed at a given time by the person who contributed to the techno. Do not hesitate to make it evolve if necessary.

