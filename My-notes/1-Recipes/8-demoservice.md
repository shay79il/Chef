# demoservice.rb

## 1. Create

```bash
mkdir /var/tmp/demorecipe

vi demoservice.rb
```

### content of `demoservice.rb`

```ruby
service 'nfs-kernel-server' do
  action :start
end
```

## 2. Check

```bash
cookstyle demoservice.rb
```

## 3. Test

```bash
chef-client --local-mode demoservice.rb --why-run
```

## 4. Run

```bash
chef-client --local-mode demoservice.rb
```
