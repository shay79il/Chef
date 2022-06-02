# demoweb.rb

## 1. Step 1 - create

```bash
mkdir /var/tmp/demorecipe

vi demoweb.rb
```

### content of `demoweb.rb`

```ruby
# Web server package installation
package 'apache2' do
  action :install
end

# Web Server file configuration
file '/var/www/html/index.html' do
  content "This is contents in file\n"
  action :create
end

# Web server service startup
service 'apache2' do
  action :start
end
```

## 2. Check

```bash
cookstyle demoweb.rb
```

## 3. Test

```bash
chef-client --local-mode demoweb.rb --why-run
```

## 4. Run

```bash
chef-client --local-mode demoweb.rb
```
