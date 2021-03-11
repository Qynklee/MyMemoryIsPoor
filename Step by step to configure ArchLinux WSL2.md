# Step by step to configure ArchLinux WSL2

### Make sure that yours WSL is WSL version 2

#### Install Arch WSL

* [ArchWSL](https://github.com/yuk7/ArchWSL)

* Init pacman-key

  ```shell
  pacman-key --init
  pacman-key --populate
  pacman-key --refresh-keys
  (if it doesnt work, try: pacman-key --keyserver hkp://pool.sks-keyservers.net --refresh-keys )
  pacman -Sy archlinux-keyring
  
  ```

* update packages to lastest versions:

  ```shell
  pacman -Syyu
  ```


#### Install zsh

```
pacman -S zsh
```

#### Create new user

```shell
useradd --create-home example_user
#setup pasword
passwd example_user
#add user to wheel group
usermod --append --groups wheel example_user
#edit sudoers file
nano /etc/sudoers
# Uncomment line: 
# ' %wheel ALL=(ALL) ALL' 
# '%wheel ALL=(ALL) NOPASSWD: ALL'
# and '%sudo ALL=(ALL) ALL'
#Save
#Test
su - example_user
```

#### Make ZSH to default shell

* In example_user:

  ```shell
  chsh -l 
  chsh -s full-patch-to-shell
  ```

  

* In sudo:

  ```shell
  chsh -l 
  chsh -s full-patch-to-shell
  ```

  

#### Config Windows Terminal open by default as example_user 

Setup in Windows Terminal setting file

```json
{
"startingDirectory": "//wsl$/arch/home/example_user",
 "commandline": "wsl -d arch -u example_user"
 }
```

#### Install Oh my ZSH and themes

