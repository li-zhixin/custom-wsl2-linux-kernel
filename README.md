# Custom WSL2 Linux Kernel

This repository is forked from [lgug2z/custom-wsl2-linux-kernel](https://github.com/lgug2z/custom-wsl2-linux-kernel).

This project uses GitHub Actions Workflows to produce and publish up-to-date builds of [WSL2-Linux-Kernel](https://github.com/microsoft/WSL2-Linux-Kernel).

The `config-wsl` is based on the official Microsoft WSL2 kernel configuration, with:
- [AppArmor](https://apparmor.net/) enabled as the default security module
- KVM (Kernel-based Virtual Machine) built-in for nested virtualization support
- [gvisor-tap-vsock](https://github.com/containers/gvisor-tap-vsock) support with TUN/TAP and VSOCK built-in

The versioning scheme of this project matches the versioning scheme used by WSL2-Linux-Kernel.

## Usage

- Download the custom kernel from the releases page
- Make sure you have saved all your work in all WSL2 instances
- Shutdown all WSL2 instances with `wsl --shutdown`
- Edit (or create) the ~/.wslconfig file on Windows
- Specify the path to the custom kernel

```ini
# For example...
[wsl2]
kernel=C:\\Users\\YOUR_USERNAME\\Downloads\\vmlinux
```

- Start a WSL2 instance
- Check that the kernel is running with `uname -sr`

```
Linux 6.6.87.1-cruz-WSL2
```

## Modification

If you want to build and publish your own custom WSL2 Linux Kernel, you can
fork this repository and make whatever configuration modifications in
[config-wsl](config-wsl). The [GitHub Actions
Workflow](.github/workflows/build.yml) will take care of the rest.

Please take care to update `CONFIG_LOCALVERSION` to distinguish your custom
kernel from this one (currently set to `-cruz-WSL2`).
