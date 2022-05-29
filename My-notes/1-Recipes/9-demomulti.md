# demomulti.rb

## 1. Create

```bash
mkdir /var/tmp/demorecipe

vi demomulti.rb
```

### content of demomulti.rb

```ruby
directory '/var/tmp/newdir' do
  owner 'shay79ill'
  group 'shay79ill'
  mode   '777'
  action :create
end

file '/var/tmp/newdir/testfile' do
  owner 'shay79ill'
  group 'shay79ill'
  mode   '777'
  content "Hello agin!\n"
  action :create
end
```

## 2. Check

```bash
cookstyle demomulti.rb
```

## 3. Test

```bash
chef-client --local-mode demomulti.rb --why-run
```

## 4. Run

```bash
chef-client --local-mode demomulti.rb
```
