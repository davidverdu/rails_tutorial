# Install Ruby 

In this tutorial I will show you how to install Ruby in your machine.

## Installation in Ubuntu 18.04

I have chosen Ubuntu 18.04 because is a popular OS for developers and also for deployments. If you do not have this OS or you just want to play, you can use [Vagrant](https://www.vagrantup.com/) with this [Vagrantfile](Vagrantfile) as a sandbox to learn. 

Even though there are many ways to install Ruby in Ubuntu, I prefer using the [rbenv](https://github.com/rbenv/rbenv) Ruby version manager tool. We will install this tool and then a version of a Ruby interpreter to be able to program in this language.

### 1. Install Ubuntu dependences
   
~~~sh
$ sudo apt-get install git gcc make libssl-dev libreadline-dev zlib1g-dev
~~~
### 2. Install rbenv from git repository

To install [rbenv](https://github.com/rbenv/rbenv) you just need to follow the instructions described in [rbenv README file](https://github.com/rbenv/rbenv/blob/master/README.md#basic-github-checkout).
The steps needed are described below:

2.1 Clone rbenv into `~/.rbenv`.

~~~sh   
$ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
~~~   

   Optionally, try to compile dynamic bash extension to speed up rbenv. Don't
   worry if it fails; rbenv will still work normally:
   
~~~sh
$ cd ~/.rbenv && src/configure && make -C src
~~~    

2.2. Add `~/.rbenv/bin` to your `$PATH` for access to the `rbenv` command-line utility.

~~~sh 
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
~~~    
    
2.3. Run `~/.rbenv/bin/rbenv init` and follow the instructions to set up rbenv integration with your shell. This is the step that will make running `ruby` "see" the Ruby version that you choose with rbenv. In this case the instructions are to add this line at the end of the `.bashrc` file:

~~~sh
eval "$(rbenv init -)"
~~~

2.4. Restart your shell so that PATH changes take effect. (Opening a new
   terminal tab will usually do it.)

2.5. Verify that rbenv is properly set up using this
   [rbenv-doctor](https://github.com/rbenv/rbenv-installer/blob/master/bin/rbenv-doctor) script:
~~~sh   
$ curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
Checking for `rbenv' in PATH: /usr/local/bin/rbenv
Checking for rbenv shims in PATH: OK
Checking `rbenv install' support: /usr/local/bin/rbenv-install (ruby-build 20170523)
Counting installed Ruby versions: none
  There aren't any Ruby versions installed under `~/.rbenv/versions'.
  You can install Ruby versions like so: rbenv install 2.2.4
Checking RubyGems settings: OK
Auditing installed plugins: OK
~~~
2.6. Install [ruby-build](https://github.com/rbenv/ruby-build#readme), which provides the
   `rbenv install` command that simplifies the process of
   [installing new Ruby versions](#installing-ruby-versions).

~~~sh
$ git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
~~~

### 3. Install Ruby 2.5.3

To see all the available Ruby versions for the Rbenv tool you can run this command:
~~~sh
$ rbenv install -l
~~~
In this tutorial I have decided to install Ruby 2.5.3 because is the latest stable version. To install this version, just run the following command:
~~~sh
$ rbenv install 2.5.3
~~~
This will take a while to download and compile.

### 4. Set Ruby 2.5.3 as our default interpreter

To use locally and globally the downloaded Ruby version, you just need to run this commands:
~~~sh
$ rbenv local 2.5.3
$ rbenv global 2.5.3
~~~

You can test if the correct Ruby is being used by running:
~~~sh
$ ruby -v
~~~
And voilà, you have Ruby installed in your system.

### BONUS: Install and use another Ruby version
You can install another Ruby version using the commands shown above. Then you can list all installed Ruby versions by the command:
~~~sh
$ rbenv versions
~~~
Swith from one version to other and check it works by typing: 
~~~sh
$ rbenv local [VERSION]
$ rbenv global [VERSION]
$ ruby -v
~~~



