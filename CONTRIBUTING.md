# Contributing to vagrant-labs

Thank you for helping improve this collection!

## Guidelines

- All environments must support both **VirtualBox** and **VMware Workstation/Fusion** providers
- Use `bento/` boxes where possible — they have the best dual-provider support
- For Windows boxes use `gusztavvargadr/` boxes
- Keep provisioning scripts idempotent (safe to run multiple times)
- Pin software versions in provisioning scripts — avoid `latest` for reproducibility
- Add a `README.md` in each environment directory with: description, access URLs, credentials
- Update the root `README.md` catalog table when adding a new environment
- Do not commit `.vagrant/` directories or generated files

## Vagrantfile Structure

Every Vagrantfile must define both providers:

```ruby
config.vm.provider "virtualbox" do |vb|
  vb.memory = 2048
  vb.cpus   = 2
end

config.vm.provider "vmware_desktop" do |vmware|
  vmware.vmx["memsize"]   = "2048"
  vmware.vmx["numvcpus"]  = "2"
end
```

## Submitting Changes

1. Fork the repository
2. Create a branch: `git checkout -b add/<environment-name>`
3. Add your environment in the correct category directory
4. Test with both providers: `vagrant up` and `vagrant up --provider=vmware_desktop`
5. Submit a Pull Request using the provided template

## Code of Conduct

Please read and follow our [Code of Conduct](CODE_OF_CONDUCT.md).
