# ChefSpec

- Chefspec is used for unit testing `in memory`
- The test is done in memory without having to run VM.
- Chefspec provides the ability to quickly test the validity
  of Chef code with a simulated convergence locally.

## Example:

> `mkdir -p spec/unit/recipe`

> `vim spec/unit/recipe/default_spec.rb`

```ruby
# spec/unit/recipe/default_spec.rb content
require 'spec_helper'

describe 'lcd_chefspec::default' do
  context 'When all attributes are default, on CentOS 7.4.1708' do
    let(:chef_run) do
      runner = ChefSpec::ServerRunner.new(platform: 'centos', version: '7.4.1708')
      runner.converge(described_recipe)
    end

    it 'converges successfully' do
      expect { chef_run }.to_not raise_error
    end

    it 'installs httpd' do
      expect { chef_run }.to  install_package('httpd')
    end

    it 'enables the httpd service' do
      expect { chef_run }.to enable_service('httpd')
    end

    it 'starts the httpd service' do
      expect { chef_run }.to start_service('httpd')
    end

  end
end
```

> `vim recipes/default.rb`

```ruby
# recipes/default.rb content
package 'httpd' do
  action :install
end

service 'httpd' do
  action [:enable, :start]
end
```
