# demouser.rb

## 1. Create

```bash
mkdir /var/tmp/demorecipe

vi demouser.rb
```

### content of `demouser.rb`

```ruby
user 'shay79ill' do
  shell '/bin/bash'
  uid   '9999'
end
```

## 2. Check

```bash
cookstyle demouser.rb
```

## 3. Test

```bash
chef-client --local-mode demouser.rb --why-run
```

## 4. Run

```bash
chef-client --local-mode demouser.rb
```
