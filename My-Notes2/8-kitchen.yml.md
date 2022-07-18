# `kitchen.yml`

```ruby
---

driver:
  # driver is what supports configuring the
  # compute instance that is used for isolated testing.
  name: vagrant

provisioner:
  # provisioner takes care of configuring the
  # compute instance provided by the driver.
  # It's for running the chef_client on the worker node
  name: chef_zero
  require_chef_omnibus: 13.4.24
  data_bags_path: test/integration/data_bags
  environments_path: test/integration/environments

verifier:
  # verifier is the testing framework
  # it tests the configuration applied by the provisioner.
  # This is most commonly a InSpec or ServerSpec,
  # both of which are included in the ChefDK/Workstation.
  name: inspec
  profiles_path: test/profiles
  format: documentation
  color: true


transport:
  #
  name: ssh
  ssh_key: ~/.ssh/dk_aws_preprod
  username: ubuntu
  connection_timeout: 10
  connection_retries: 5

platforms:

- name: ubuntu-20.04

suites:
  # Suites is a collection of test suites,
  # With each suite_name grouping defining an aspect of a cookbook to be tested.
  # Each suite_name must specify a run-list
  - name: default
    run_list:
      - recipe[partition]
    verifier:
    inspec_tests:
      - test/integration/default
    attributes:


  - name: default
    # EXAMPLE runlist needed to format data disks properly
    run_list:
      - recipe[partition]
    attributes:
      # EXAMPLE attributes allows us to override default values
      partition:
        target_block_device: "/dev/nvme1n1"
    # Add additional paths in the inspec tests to test different directories with different goals
    verifier:
      name: inspec
      format: documentation
      color: true
      inspec_tests:
        - path: test/integration/default
```
