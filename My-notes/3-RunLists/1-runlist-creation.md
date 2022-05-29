# RunLists

```bash
# The following command creates a runlist
chef-client --runlist "recipe[cookbook-Name::Recipe-Name]"
```

## Chef RunList composed from 4 steps

- Create - 'chef generate cookbook `<cookbook-Name>`'
- Check - 'cookstyle `<cookbook-Name>`'
- Test - 'chef-client --local-mode --runlist "recipe[webserver::default]" --why-run'
- Run - 'chef-client --local-mode --runlist "recipe[webserver::default]"'

```bash
# To refer to the default recipe omit the 'recipe-name'
chef-client --local-mode --runlist "recipe[webserver]"
```


## There are 4 types of RunLists

### 1. With default recipe 'default.rb'

```bash
chef-client --local-mode --runlist "recipe[webserver::default]" --why-run
```

### 2. Without any recipe name

```bash
chef-client --local-mode --runlist "recipe[webserver]" --why-run
```

### 3. Recipe with a different name

```bash
# No need to add the '.rb' extension
# 'apache2' is just an example
chef-client --local-mode --runlist "recipe[webserver::apache2]" --why-run
```

### 4. Multiple recipes together

```bash
# To define which ORDER the recipes will run
# Just place the recipes one after the other
# In the order we want
chef-client --local-mode --runlist "recipe[webserver::default],recipe[webserver::file],recipe[webserver::apache2]"
```
