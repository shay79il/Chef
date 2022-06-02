# Chef cookbook

## Composed from 4 steps

## 1. Create

```bash
# Create a cookbook skeleton
chef generate cookbook webserver
```

## 2. Check

```bash
# check the cookbook
cookstyle webserver
```

## 3. Test

```bash
# check the cookbook
chef-client --local-mode "recipe[webserver]" --why-run
```

## 4. Run

```bash
# Run the cookbook
chef-client --local-mode "recipe[webserver]"
```

# For help

## `chef generate --help`
