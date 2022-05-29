# demofile.rb

## 1. Create

```bash
mkdir /var/tmp/demorecipe

vi demofile.rb
```

### content of demofile.rb

```ruby
file '/var/tmp/testfile' do
  owner 'shay79ill'
  group 'shay79ill'
  mode   '777'
  action :create
end
```

## 2. Check

```bash
cookstyle demofile.rb
```

## 3. Test

```bash
chef-client --local-mode demofile.rb --why-run
```

## 4. Run

```bash
chef-client --local-mode demofile.rb
```
