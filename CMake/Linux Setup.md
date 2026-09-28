ref: [microslop -> CMake in Linux](https://learn.microsoft.com/en-us/cpp/linux/cmake-linux-project?view=msvc-170), [microslop -> installing the linux workload](https://learn.microsoft.com/en-us/cpp/linux/download-install-and-setup-the-linux-development-workload?view=msvc-170)

for doing CMake in linux you need to install [WSL on Windows](https://learn.microsoft.com/en-us/windows/wsl/setup/environment) to be able to build for linux. When setting up wsl, make sure to have a distributor to use, for me I use Ubuntu-24.04. for other options you can do:
```bash 
sudo wsl --list --online
```
to reveal all the different distributors of wsl. 

Once done, install the necessary packages on the remote system using: 
```bash 
sudo apt-get install 'package name'
```

Which each package is defined in the [documentation](https://learn.microsoft.com/en-us/cpp/linux/download-install-and-setup-the-linux-development-workload?view=msvc-170)
