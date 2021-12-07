# Working with REDH Tools, Notebooks, and Pipelines 

## Mac Environment
### Base System Setup

1. XCode install (must be installed from App Store) 
1. Install Brew `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

### Recommended ENV setup 

* Copy your global zshrc file to local one, use the following command
  ```shell
  cat /etc/zshrc > ~/.zshrc
  ```
* Make sure to add the following environmental variables to your local zshrc file in your home directory.
  ```shell
  # Local user bin file for scripts and binaries
  export PATH=~/bin:$PATH
  
  # configure zlib
  export LDFLAGS="-L/usr/local/opt/zlib/lib"
  export CPPFLAGS="-I/usr/local/opt/zlib/include"
  ```
### Setup for Snowflake

* Download the binaries from: https://sfc-repo.snowflakecomputing.com/snowsql/bootstrap/1.2/darwin_x86_64/index.html
* Add Snowflake Binaries to PATH, add the following to your .zshrc
  ```shell
  export PATH=/Applications/SnowSQL.app/Contents/MacOS:$PATH
  ```

### Setup Python for Virtual Environments

**NOTE**: We highly recommend using virtual environments, and with the Mac environment we also strongly encourage
you to use `pyenv`

#### Install PyEnv with Brew
```shell
brew install pyenv
```

#### Example of Installing Python 3.9.5
```shell
pyenv install 3.9.5
```
#### Installing VirtualEnv
```shell
pip install virtualenvwrapper
```

##### Use  easy_install to install pip
If pip does not work, install pip with easy_install
```shell
easy_install pip
```
  
You should have the ability to create a virtual environment using a specific Python version
installed in your home directory instead of relying on your system's python

### Creating a VirtualEnv
* `cd` to your working directory
* Create a virtualenv
* If you have more than one python version installed at global system level, you may have to remove other versions except for the ones `which python` using these [instructions](https://www.techjunkie.com/macos-uninstall-python3/)
* You may have to downgrade "stevedore" package on python2.7 for "virtualenvwrapper" to work. The specific version of stevedore used was "1.32.0". 
* Use easy_install if you have multiple python version to ensure system python libraries are used
* After creating the .virtualenv file add the following command to your .zshrc 
  ```shell
  source ~/.virtualenv
  ```
  ```shell
  mkvirtualenv -p ~/.pyenv/version/<PYTHON_VERSION>/bin/python MY_VIRTUALENV
  setvirtualenv
  ```