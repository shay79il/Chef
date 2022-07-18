# Define an `attribute`

> `chef generate attribute default`

> `vim attribute/default.rb`

```ruby
# attribute/default.rb content
default['greeting'] = 'Hello'
```

# Define a `template`

## Create `erb` file for `index.html` file

> `chef generate template index.html`

> `vim attribute/index.html.erb`

```ruby
# attribute/index.html.erb content
# fqdn - fully-qualified domain name
<%= @greeting %> <%= @greeting_scope %> from <%= @fqdn %>
```

# Define a `recipe` from a template

> `vim recipe/default.rb`

```ruby
# recipe/default.rb content
template '/var/www/html/index.html' do
  source 'index.html.erb'
  owner 'apache'
  group 'apache'
  variables(
    greeting: node['greeting']
    greeting_scope: 'World'
    fqdn: node['fqdn']
  )
end
```
