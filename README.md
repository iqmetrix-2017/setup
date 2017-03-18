#Develop With Passion® - Developer BootCamp Setup

##The following setup should take no more than 20 minutes to complete, assuming that you are not dealing with a dial-up internet connection!

##Network Security Considerations

* Make sure that you have access to port 443 for github ssh operations (have your network admins open this up for the week if necessary, to avoid any unecessary complications) 

##Programs That Should Be Installed Prior to following these instructions

###Required
* VS2013/2015 - I'm using VS 2015 Community Edition

##The main programs you will be installing in this setup are:

* Git
* Ruby
* MingW

#Required Setup

The following is the setup that you WILL need to perform to configure all necessary prerequisites to be able to enjoy the week. If you have any questions, please do not hesitate to contact [me](mailto:jp@developwithpassion.com)

##Make sure that you have configured windows to show all hidden files and folders

##Create the utility folder

1. Open up windows explorer and navigate to your C:\ drive
2. Create a new folder at the root of C:\ called utils (all lowercase). All of the tools we will install for the week will go into here.

##Get setup at [Github](http://github.com)

* [Sign up](https://github.com/signup/free) for a free account at github.com. My recommendation is to use an all lowercase username.

##Install Ruby

* Install [Ruby](https://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-2.2.6-x64.exe), yes the specific version in this link, not the newest.

* Configure according to the following screenshots:

![ruby_setup_1](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/ruby_setup_1.png)

* Once the install has completed, verify your installation by opening up a command prompt and typing in: ruby -v. You should see:
  * ruby 2.2.6p369 [version and date information]

##Install Git for windows

1. Install the Git for windows from [here](https://github.com/git-for-windows/git/releases/download/v2.12.0.windows.1/Git-2.12.0-64-bit.exe)

* Configure according to the following screenshots:

![git_setup_part_1](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/git_setup_part_1.png)
![git_setup_part_2](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/git_setup_part_2.png)
![git_setup_part_3](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/git_setup_part_3.png)
![git_setup_part_4](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/git_setup_part_4.png)
![git_setup_part_5](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/git_setup_part_5.png)
![git_setup_part_6](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/git_setup_part_6.png)

##Setup your git ssh authentication key

1. Open up a git bash prompt
2. Enter the following command:

    ```bash
    ssh-keygen -t rsa -C your_email_address  
    ```
   
   Accept the defaults for the remaining prompts  (leave the passphrase blank).  
3. Navigate to the folder where your ssh key was created (by default your profile ssh folder C:\Users\your_user_name\\.ssh)
4. Open the file id_rsa.pub and copy the contents to the clipboard.
5. Login to your account at [github](https://github.com/login).
6. Navigate to your [ssh settings](https://github.com/settings/ssh)
7. Click on the Add SSH Key Button
8. Give your key a title and paste the public key that is in your clipboard from step 4 into the Key text entry:

![ssh key entry](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/add_ssh_key.png)

##Verify that your git ssh authentication works

1. Open up a git bash prompt
2. Enter the following command:

    ```bash
    ssh -v git@ssh.github.com
    ```
3. If prompted to cache the server identity, type yes.
4. If you have setup your ssh settings correctly the bottom part of the command output should look similar to the following:

![successful authentication](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/git_authentication.png)

##Clone this setup repository

1. Open up a git bash prompt and type the following commands:

```bash
cd /c
mkdir course
cd course
git clone https://github.com:iqmetrix-2017/setup.git [enter]
```

At the completion of the last command you should have a copy of this repository on your local machine.

##Install Mingw

Open up a git bash prompt and type the following commands:

```bash
cd /c/course/setup
explorer .
```
Double click the mingw-get-inst-20111118.exe installer and install using the following screenshots:

![mingw_setup_part_1](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/mingw_setup_part_1.png)
![mingw_setup_part_2](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/mingw_setup_part_2.png)
![mingw_setup_part_3](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/mingw_setup_part_3.png)
![mingw_setup_part_4](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/mingw_setup_part_4.png)
![mingw_setup_part_5](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/mingw_setup_part_5.png)

##Finalize setup

The following steps will ensure that you have your git environment setup correctly for the class. If you already have existing git configuration that you use on a regular basis, either make your changes manually to match the recommended settings, or create a backup of your existing configuration and restore it after the class.

Open up a git bash prompt and type in the following commands:

```bash
cd /c/course/setup 
gem uninstall bundler   # Answer yes to any prompts if you are prompted
gem install bundler
bundle install
thor setup
```

Upon running the last command you will be prompted to make changes to a settings file that has been generated based on your username. It should be in the root of this repo folder with the name [ your-logged-in-name-without-spaces-or-path-symbols-all-lowercase ].settings.

Open up your settings file in your favourite text editor and make sure all of the settings are correct. If you have followed along correctly to this point (by using the specified install paths and key generation procedure etc), the only settings you should need to change are in the git section of the configuration file. Change the following: 

* name
* email

Take a look at the sample_settings file in this directory, if you are unsure how to make the changes. It uses fake values for the values you need to change.

If you deviated from the recommended setup you will have to tweak extra settings as needed. The config file is fairly self explanatory, so hopefully you can figure it out if you made your own custom changes. Make your change(s) and save the file.


Continue to rerun the following command:

```bash
thor setup
```

This task will do the following:

* Setup a sane ~/.gitconfig that contains the email you provided and your name, along with some other aliases and a setting that is essential for our work during the week.
* Copies some basic bash dotfiles into your home folder, this correctly sets up the ssh agent to use the key you generated/provided earlier.
* Configures the mingw path

##Verify that your git ssh authentication works using the new config that has been created

1. Open up a git bash prompt
2. Enter the following command:

    ```bash
    ssh -v github
    ```
3. If prompted to cache the server identity, type yes.
4. Once again, the command output should look similar to the following:

![successful authentication](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/git_authentication.png)

##Verify Installs

Open up a git bash prompt and type the following:

```bash
ruby -v
```
You should see a ruby version, if you don't see anything you may need to repeat the steps above as you may have missed a step.

##Fork the project repositories for the week

1. Login to your account at [github](https://github.com/login)
2. Navigate to the following url: http://github.com/iqmetrix-2017 
3. Click on the prep repository: ![repository](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/github_shawaugp.png)
4. Click on the fork button to create your own copy of this repository <br>![fork](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/github_fork.png)

## Checkout your local copies of the code

1. Open up a git bash prompt and type the following commands:
    ```bash
    cd /c/course 
    git clone github:[your github user name]/prep.git
    ```
    Assuming your github username is jp the commands would look as follows:

    ```bash
    git clone github:jp/prep.git
    ```

2. Once you have completed cloning the repositories your course folder should look as follows:

![checked out directory](https://raw.githubusercontent.com/iqmetrix-2017/setup/master/images/checked_out_directory.png)

##Finalization

* Last steps of setup will be completed on Monday morning!
