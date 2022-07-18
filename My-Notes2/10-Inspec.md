# InSpec

- Inspec functions as a `verifier` in `kitchen.yml`
- It serves as the test framework for integration testing
- It allows to verify the configuration in a test environment

> Example:

```ruby
describe package('httpd') do
  it { should be_installed }
end
```

- Tests should be in `test/integration/<suite_name>` folder
  - When `<suite_name>` is identical name listed in `kitchen.yml`

## `kitchen.yml` sample

```ruby
---

driver:
  name: vagrant

provisioner:
  name: chef_zero
  always_update_cookbooks: true
  product_name: "chef"
  product_version: "13.8.5"

verifier:
  name: inspec

transport:
  name: ssh
  ssh_key: ~/.ssh/dk_aws_preprod
  username: ubuntu
  connection_timeout: 10
  connection_retries: 5

platforms:
  - name: ubuntu-20.04

suites:
  - name: default
    run_list:
      - recipe[lcd_inspec::default]
    verifier:
      inspec_tests:
        - test/integration/default
    attributes:
```

> `vim recipe/default.rb`

```ruby
# recipe/default.rb content
['net-tools', 'httpd'].each do |pkg|
  package pkg do
    action :install
  end
end
```

> `mkdir -p test/integration/default`

> `vim test/integration/default/default_test.rb`

```ruby
# test/integration/default/default_test.rb content
['net-tools', 'httpd'].each do |pkg|
  describe package(pkg) do
    it {should be_installed}
  end
end
```
