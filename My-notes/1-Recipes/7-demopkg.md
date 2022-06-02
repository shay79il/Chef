# demopkg.rb

## 1. Create

```bash
mkdir /var/tmp/demorecipe

vi demopkg.rb
```

### content of `demopkg.rb`

```ruby
package 'nfs-kernel-server' do
  action :install
end
```

## 2. Check

```bash
cookstyle demopkg.rb
```

## 3. Test

```bash
chef-client --local-mode demopkg.rb --why-run
```

## 4. Run

```bash
chef-client --local-mode demopkg.rb
```
