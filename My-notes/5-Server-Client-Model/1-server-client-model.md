# Server Client Model

## We hve 4 steps

### 1. Connect the Chef-Workstation to Chef-Server

```bash
knife ssl fetch
knife ssl check
```

### 2. Create the code and test it

```bash
# Generate cookbook structure
chef generate cookbook <cookbook-name>

# Check / validate cookbook
cookstyle <cookbook-name>

# Test the code localy on the Chef-Workstation
chef-client --local-mode --runlist "recipe[webserver]"
```

### 3. Upload the code

```bash
# Upload cookbook to Chef-Server
chef cookbook upload <cookbook-name>
```

### 4. Create RunList

```bash
# Watch the Nodes/Chef-Clients connected to the Chef-Server
knife node list

# Get all info on the NODE
# Including all its RunList and recipes
knife node show NODE_NAME
```

### 5. Optional step - Add a new cookbook

```bash
# 1. Generate new cookbook
chef generate cookbook motd

# 2. Update its 'default.rb' file
file '/etc/motd' do
  content "This is a sample message of the day using Chef Automation\n"
  action :create
end

# 3. Run test before uploading to Chef Server
chef-client --local-mode --runlist "recipe[motd]" --why-run

# 4. Add the NEW cookbook to the client RunList
knife node run_list add client.example.com "recipe[motd]"

# 5. Upload the NEW cookbook motd to the Chef-Server
knife cookbook upload motd
```

### 6. Apply Code

```bash
# Test chef-client on the client Node
knife ssh --ssh-user ubuntu --ssh-identity-file "$AWS_SSH" 'name:client.example.com' 'sudo chef-client --why-run'

# Run chef-client on the client Node
knife ssh --ssh-user ubuntu --ssh-identity-file "$AWS_SSH" 'name:client.example.com' 'sudo chef-client'
```
