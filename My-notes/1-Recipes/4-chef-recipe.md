# Chef Recipe

## Composed from 4 steps

1. Create - '.rb' files (rb stands for ruby)
2. Check - cookstyle <file.rb>
3. Test - 'chef-client --local-mode --why-run <file.rb>'
4. Run - 'chef-client --local-mode <file.rb>'

# Example: demouser.rb

## 1. Create

```bash
mkdir /var/tmp/demorecipe

vi demouser.rb
```

**Content of 'demouser.rb'**

```ruby
user 'shay79ill' do
  shell '/bin/bash'
  uid   '9999'
end
```

---

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
