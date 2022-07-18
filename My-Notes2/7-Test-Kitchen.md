# [Test Kitchen](https://docs.chef.io/workstation/kitchen/)

The key concepts in Test Kitchen are:

- A platform is the operating system or target environment on which a cookbook is to be tested
- A suite is the Chef Infra Client configuration, a Policyfile or run-list, and (optionally) node attributes
- An instance is the combination of a specific platform and a specific suite, with each instance being assigned an auto-generated name
- A driver is the lifecycle that implements the actions associated with a specific instance—create the instance, do what is needed to converge on that instance (such as installing Chef Infra Client, uploading cookbooks, starting a Chef Infra Client run, and so on), setup anything else needed for testing, verify one (or more) suites post-converge, and then destroy that instance
- A provisioner is the component on which the Chef Infra Client code will be run, either using chef-zero or chef-solo via the chef_zero and chef_solo provisioners, respectively

---

## Kitchen commands

`kitchen setup`

- Ensure the instance is prepared for testing.
- So depending on your test framework, this may require the
  installation and preparation of tools on the instance.

---

`kitchen verify`

- Execute tests defined within the suites on your instances
  - This phase invokes the inspec test framework to analyze the
    state, to determine if the conditions on the instance satisfies those tests.
- The output associated with kitchen verify will let you know
  how many tests have passed or failed.

---

`kitchen test`

- Destroys the instance if it exists
- Creates the instance
- Converges the instance
- Verifies the instance with InSpec
- Destroys the instance

---

`kitchen converge`

- Installing Infra Chef Client
- Uploading cookbooks
- Starting a Chef Infra Client run
- Executes the `run_list` in `kitchen.yml`

---

`kitchen login <instance>`

Login to the converged instance

## Kitchen workflow

1. Setup `kitchen.yml`
2. Write relevant tests
3. Run `kitchen verify` (create + converge)
4. Examine failures
5. Fix test
6. Run `kitchen converge`
7. Run `kitchen verify`
8. Repeat from step 2
9. Run `kitchen destroy`
