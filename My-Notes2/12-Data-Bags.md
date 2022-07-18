# Data-Bags

- Data-Bags are containers for information about
  the infrastructure that is NOT associated with a node.
- Data-Bags provide an external source of information
  to be used in recipes and search functionality
- A Data bag is a `global variable` that is stored as
  JSON data and is accessible via a Chef server

## Knife commands:

- `knife data bag create` BAG [ITEM] (options)
- `knife data bag delete` BAG [ITEM] (options)
- `knife data bag edit` BAG [ITEM] (options)
- `knife data bag from file` BAG FILE|FOLDER [FILE|FOLDER..] (options)
- `knife data bag list` (options)
- `knife data bag show` BAG [ITEM] (options)

## Example:

> Create a data bag

```bash
# admins  - name of the data bag
# joe     - name of the item within the admins data bag
knife data bag create admins joe
```

> Create a data bag

```bash
# admins  - name of the data bag
# joe     - name of the item within the admins data bag
knife data bag from file admins /path/to/joe.json
```

> While `joe.json` content is

```json
{
  "id": "joe",
  "uid": "1001",
  "gid": "developers",
  "shell": "/bin/bash",
  "comment": "Joe"
}
```

## Searching for an ITEM in a DATA BAG

```bash
# knife search [DATA BAG] [ITEM]
knife search admins "id:joe"
knife search admins "NOT id:tom"
knife search admins "id:tom OR id:joe"
knife search admins "*:*"
knife search admins "id:admin*"
```

## How to refer to a DATA BAG in the code

```ruby
data_bag('admins')
data_bag_item('admins', 'joe')

# DATA BAG can be assigned as a variable
admins = data_bag('admins')
admins.each do |login|
  admin = data_bag_item('admins', 'login')
  group admin['gid']
end

admins = []
search(:admins, "gid:administrators").each do |admin|
  group admin['gid']
  login = admin["id"]
  admins << login
  home = "/hom/#{login}"

  user(login) do
    uid           admin['uid']
    gid           admin['gid']
    shell         admin['shell']
    comment       admin['comment']
    home          home
    manage_home   true
  end
end
```
