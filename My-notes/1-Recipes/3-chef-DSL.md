# Chef DSL - Domain Specific Language

```ruby
<Resource Type> '<NAME'> do
  <Attribute> '<Value>'
  <Attribute> '<Value>'
  <Attribute> '<Value>'

  <Action> : <Value>
end
```

## Example:

```ruby
# Web server package installation
package 'httpd' do
  action :install
end

# Web Server file configuration
file '/var/www/html/index.html' do
  content "This is contents in file\n"
  action :create
end

# Web server service startup
service 'httpd' do
  action :start
end
```
