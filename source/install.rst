
.. _install:

============
Installation
============

The *EMQ X* broker is cross-platform, it can be deployed on Linux, FreeBSD, Mac and Windows.

.. NOTE::

    It is recommended to deploy EMQ X on Linux for production environment.

.. _install_download:

*EMQ X* Package Download
-------------------------

Each version of the EMQ X broker will release packages of CentOS, Ubuntu, Debian, openSUSE, FreeBSD, macOS, Windows platform and Docker images.

Download address: https://www.emqx.io/downloads

.. _emqx.io: https://www.emqx.io/downloads/broker?osType=Linux
.. _github: https://github.com/emqx/emqx/releases

CentOS
------

+ CentOS6.X
+ CentOS7.X

Install via Repository
>>>>>>>>>>>>>>>>>>>>>>>

1.  Install the required dependencies

    .. code-block:: console

        $ sudo yum install -y yum-utils device-mapper-persistent-data lvm2

2.  Set up a stable repository, taking the CentOS7 as an example.

    .. code-block:: console

        $ sudo yum-config-manager --add-repo https://repos.emqx.io/emqx-ce/redhat/centos/7/emqx-ce.repo

3.  Install the latest version of EMQ X

    .. code-block:: console

        $ sudo yum install emqx

    .. NOTE::If prompted to accept the GPG key, please verify that the key's fingerprint matches fc84 1ba6 3775 5ca8 487b 1e3c c0b4 0946 3e64 0d53 and accept the fingerprint if it matches.


4.  Install a specific version of EMQ X

    1.  Query available version

        .. code-block:: console

            $ yum list emqx --showduplicates | sort -r

            emqx.x86_64                     4.0.0-1.el7                        emqx-stable
            emqx.x86_64                     3.0.1-1.el7                        emqx-stable
            emqx.x86_64                     3.0.0-1.el7                        emqx-stable

    2.  Install a specific version based on the version string in the second column, such as 4.0.0

        .. code-block:: console

            $ sudo yum install emqx-4.0.0

5.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx 4.0.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx v4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

6.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via rpm
>>>>>>>>>>>>>>>>

1.  Select the CentOS version via emqx.io or github and download the rpm package for the EMQ X version to be installed.

2.  Install EMQ X

    .. code-block:: console

           $ sudo rpm -ivh emqx-centos7-v4.0.0.x86_64.rpm

3.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx 4.0.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx v4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

4.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1. Select the CentOS version via emqx.io or github and download the zip package for the EMQ X version to be installed.

2.  Unzip package

    .. code-block:: console

       $ unzip emqx-centos7-v4.0.0.zip

3.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx 4.0.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx v4.0.0 is running

Ubuntu
------

+ Bionic 18.04 (LTS)
+ Xenial 16.04 (LTS)
+ Trusty 14.04 (LTS)
+ Precise 12.04 (LTS)

Install via Repository
>>>>>>>>>>>>>>>>>>>>>>>

1.  Install the required dependency

    .. code-block:: console

        $ sudo apt update && sudo apt install -y \
            apt-transport-https \
            ca-certificates \
            curl \
            gnupg-agent \
            software-properties-common

2.  Add the GPG key for EMQ X

    .. code-block:: console

        $ curl -fsSL https://repos.emqx.io/gpg.pub | sudo apt-key add -

    Validate key

    .. code-block:: console

        $ sudo apt-key fingerprint 3E640D53

        pub   rsa2048 2019-04-10 [SC]
            FC84 1BA6 3775 5CA8 487B  1E3C C0B4 0946 3E64 0D53
        uid           [ unknown] emqx team <support@emqx.io>

3.  Use the following command to set up the stable repository. If unstable repo is also needed, add the word 'unstable' after 'stable' in the following command.

    .. code-block:: console

        $ sudo add-apt-repository \
            "deb [arch=amd64] https://repos.emqx.io/emqx-ce/deb/ubuntu/ \
            $(lsb_release -cs) \
            stable"

    .. NOTE:: The lsb_release -cs subcommand returns the name of the Ubuntu distribution, such as xenial. Sometimes, in a distribution like Linux Mint, you might need to change $(lsb_release -cs) to the parent Ubuntu distribution. For example, if you are using Linux Mint Tessa, you can use bionic. EMQ X does not provide any guarantees for untested and unsupported Ubuntu distribution.

4.  Update apt package index

    .. code-block:: console

        $ sudo apt update

5.  Install the latest version of EMQ X

    .. code-block:: console

        $ sudo apt install emqx

    .. NOTE:: In the case where multiple EMQ X repositories are enabled, and the apt install and apt update commands is not specified with a version number, the latest version of EMQ X is installed. This could be a problem for users with stability needs.

6.  Install a specific version of EMQ X

    1.  Query available version

        .. code-block:: console

            $ sudo apt-cache madison emqx

            emqx |      4.0.0 | https://repos.emqx.io/emqx-ce/deb/ubuntu bionic/stable amd64 Packages
            emqx |      3.0.1 | https://repos.emqx.io/emqx-ce/deb/ubuntu bionic/stable amd64 Packages
            emqx |      3.0.0 | https://repos.emqx.io/emqx-ce/deb/ubuntu bionic/stable amd64 Packages


    2.  Install a specific version using the version string from the second column, such as 4.0.0

        .. code-block:: console

            $ sudo apt install emqx=4.0.0

7.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx 4.0.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx v4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

8.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via deb Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the Ubuntu version via emqx.io or github and download the deb package for the EMQ X version to be installed.

2.  Install EMQ X

    .. code-block:: console

           $ sudo dpkg -i emqx-ubuntu18.04-v4.0.0_amd64.deb

3.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx 4.0.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx v4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

4.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the Ubuntu version via emqx.io or github and download the zip package for the EMQ X version to be installed.

2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-ubuntu18.04-v4.0.0.zip

3.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx 4.0.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx v4.0.0 is running

Debian
-------

+ Stretch (Debian 9)
+ Jessie (Debian 8)

Install via Repository
>>>>>>>>>>>>>>>>>>>>>>>

1.  Install the required dependency

    .. code-block:: console

        $ sudo apt update && sudo apt install -y \
            apt-transport-https \
            ca-certificates \
            curl \
            gnupg-agent \
            software-properties-common

2.  Add the GPG key for EMQ X

    .. code-block:: console

        $ curl -fsSL https://repos.emqx.io/gpg.pub | sudo apt-key add -

    Validate the key

    .. code-block:: console

        $ sudo apt-key fingerprint 3E640D53

        pub   rsa2048 2019-04-10 [SC]
            FC84 1BA6 3775 5CA8 487B  1E3C C0B4 0946 3E64 0D53
        uid           [ unknown] emqx team <support@emqx.io>

3.  Use the following command to set up the stable repository. If unstable repo is also needed, add the word 'unstable' after 'stable' in the following command.

    .. code-block:: console

        $ sudo add-apt-repository \
            "deb [arch=amd64] https://repos.emqx.io/emqx-ce/deb/debian/ \
            $(lsb_release -cs) \
            stable"

    .. NOTE:: The lsb_release -cs subcommand returns the name of the Debian distribution, such as helium. Sometimes, in a distribution like BunsenLabs Linux, you might need to change $(lsb_release -cs) to the parent Debian distribution. For example, if you are using BunsenLabs Linux Helium, you can use stretch. EMQ X does not provide any guarantees for untested and unsupported Debian distribution.

4.  Update apt package index

    .. code-block:: console

        $ sudo apt update

5.  Install the latest version of EMQ X

    .. code-block:: console

        $ sudo apt install emqx

    .. NOTE:: In the case where multiple EMQ X repositories are enabled, and the apt install and apt update commands is not specified with a version number, the latest version of EMQ X is installed. This is a problem for users with stability needs.

6.  Install a specific version of EMQ X

    1.  Query available version

        .. code-block:: console

            $ sudo apt-cache madison emqx

            emqx |      4.0.0 | https://repos.emqx.io/emqx-ce/deb/debian stretch/stable amd64 Packages
            emqx |      3.0.1 | https://repos.emqx.io/emqx-ce/deb/debian stretch/stable amd64 Packages
            emqx |      3.0.0 | https://repos.emqx.io/emqx-ce/deb/debian stretch/stable amd64 Packages


    2.  Install a specific version using the version string from the second column, such as 4.0.0

        .. code-block:: console

            $ sudo apt install emqx=4.0.0

7.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx 4.0.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx v4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

8.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via deb Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the Debian version via emqx.io or github and download the deb package for the EMQ X version to be installed.

2.  Install EMQ X

    .. code-block:: console

           $ sudo dpkg -i emqx-debian9-v4.0.0_amd64.deb

3.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx 4.0.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx v4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

4.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the Debian version via emqx.io or github and download the zip package for the EMQ X version to be installed.

2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-debian9-v4.0.0.zip

3.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx 4.0.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx v4.0.0 is running

macOS
------

.. _Homebrew: https://brew.sh/

Install via Homebrew
>>>>>>>>>>>>>>>>>>>>>

1.  Add tap of EMQ X

    .. code-block:: console

        $ brew tap emqx/emqx

2.  Install EMQ X

    .. code-block:: console

        $ brew install emqx

3.  Start EMQ X

    .. code-block:: console

        $ emqx start
        emqx 4.0.0 is started successfully!

        $ emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx v4.0.0 is running

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select the EMQ X version via emqx.io or github and download the zip package to install.

2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-macos-v4.0.0.zip

3.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx 4.0.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx v4.0.0 is running

Windows
--------

1.  Select the Windows version via emqx.io or github and download the .zip package to install.

2.  Unzip the package

3.  Open the Windows command line window, change the directory to the program directory, and start EMQ X.

    .. code-block:: console

        cd emqx/bin
        emqx start

openSUSE
---------

+ openSUSE leap

Install via Repository
>>>>>>>>>>>>>>>>>>>>>>>

1.  Download the GPG public key and import it.

    .. code-block:: console

        $ curl -L -o /tmp/gpg.pub https://repos.emqx.io/gpg.pub
        $ sudo rpmkeys --import /tmp/gpg.pub

2.  Add repository address

    .. code-block:: console

        $ sudo zypper ar -f -c https://repos.emqx.io/emqx-ce/redhat/opensuse/leap/stable emqx

3.  Install the latest version of EMQ X

    .. code-block:: console

        $ sudo zypper in emqx

4.  Install a specific version of EMQ X

    1. Query available version

        .. code-block:: console

            $ sudo zypper pa emqx

            Loading repository data...
            Reading installed packages...
            S | Repository | Name | Version  | Arch
            --+------------+------+----------+-------
              | emqx       | emqx | 4.0.0-1  | x86_64
              | emqx       | emqx | 3.0.1-1  | x86_64
              | emqx       | emqx | 3.0.0-1  | x86_64

    2.  Use Version column to install a specific version, such as 4.0.0

        .. code-block:: console

            $ sudo zypper in emqx-4.0.0

5.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx 4.0.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx v4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

6.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via rpm Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select openSUSE via emqx.io or github and download the rpm package for the EMQ X version to be installed.

2.  Install EMQ X and change the path below to the path where you downloaded the EMQ X package.

    .. code-block:: console

           $ sudo rpm -ivh emqx-opensuse-v4.0.0.x86_64.rpm

3.  Start EMQ X

    +   Directly start

        .. code-block:: console

                $ emqx start
                emqx 4.0.0 is started successfully!

                $ emqx_ctl status
                Node 'emqx@127.0.0.1' is started
                emqx v4.0.0 is running

    +   systemctl start

        .. code-block:: console

                $ sudo systemctl start emqx

    +   service start

        .. code-block:: console

                $ sudo service emqx start

4.  Configuration file path

    + Configuration file path: ``/etc/emqx``

    + Log file path: ``/var/log/emqx``

    + Data file path: ``/var/lib/emqx`

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select openSUSE via emqx.io or github and download the zip package for the EMQ X version to be installed.


2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-opensuse-v4.0.0.zip

3.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx 4.0.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx v4.0.0 is running

FreeBSD
--------

+ FreeBSD 12

Install via zip Package
>>>>>>>>>>>>>>>>>>>>>>>>

1.  Select FreeBSD via emqx.io or github and download the zip package for the EMQ X version to be installed.

2.  Unzip the package

    .. code-block:: console

       $ unzip emqx-freebsd12-v4.0.0.zip

3.  Start EMQ X

    .. code-block:: console

        $ ./bin/emqx start
        emqx 4.0.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx v4.0.0 is running

Docker
-------

.. _Docker Hub: https://hub.docker.com/r/emqx/emqx
.. _EMQ X Docker: https://github.com/emqx/emqx-docker

1.  Get docker image

    +   Through `Docker Hub`_

        .. code-block:: console

            $ docker pull emqx/emqx:v4.0.0

    +    Download the docker image via emqx.io or github manually and load it manually

        .. code-block:: console

            $ wget -O emqx-docker.zip https://www.emqx.io/downloads/v3/latest/emqx-docker.zip
            $ unzip emqx-docker.zip
            $ docker load < emqx-docker-v4.0.0

2.  Start the docker container

    .. code-block:: console

        $ docker run -d --name emqx31 -p 1883:1883 -p 8083:8083 -p 8883:8883 -p 8084:8084 -p 18083:18083 emqx/emqx:v4.0.0

For more information about EMQ X Docker, please check `Docker Hub`_ or `EMQ X Docker`_.

Source Code Compilation and Installation
-----------------------------------------

Environmental requirements
>>>>>>>>>>>>>>>>>>>>>>>>>>>

EMQ X broker is developed on the Erlang/OTP platform. The project is maintained and managed on GitHub. The source code compilation relies on the Erlang environment and the git client.

.. NOTE:: EMQ X relies on the Erlang R21.2+ version

Erlang Install: http://www.erlang.org/

Git client: http://www.git-scm.com/

Compile and Install EMQ X
>>>>>>>>>>>>>>>>>>>>>>>>>>>

1.  Get the source code

    .. code-block:: bash

        $ git clone -b v4.0.0 https://github.com/emqx/emqx-rel.git

2.  Set environment variables

    .. code-block:: bash

        $ export EMQX_DEPS_DEFAULT_VSN=v4.0.0

3.  Compile


    .. code-block:: bash

        $ cd emqx-rel && make

4.  Start EMQ X

    .. code-block:: bash

        $ cd emqx-rel/_rel/emqx
        $ ./bin/emqx start
        emqx v4.0.0 is started successfully!

        $ ./bin/emqx_ctl status
        Node 'emqx@127.0.0.1' is started
        emqx 4.0.0 is running

Windows source code compilation and installation
-------------------------------------------------

Erlang install: http://www.erlang.org/

scoop install: http://scoop.sh/

After the scoop is installed, the Git, Make and erlang can be installed using the scoop package management tool.

.. code-block:: bash

        scoop install git make curl erlang

After the environment is ready, the code can be compiled.

rebar3 install:

.. code-block:: bash

        git clone https://github.com/erlang/rebar3.git

        cd rebar3

        bootstrap

After rebar3 is built successfully, add rebar3 path into the environment path of windows

.. code-block:: bash

        git clone -b -b v4.0.0 https://github.com/emqx/emqx-rel.git

        cd emqx-relx && make

        cd _rel/emqx && ./bin/emqx start

Star the compiled EMQ X on the console:

.. code-block:: bash

        cd _rel/emqx/bin
        emqx console

Register windows service:

.. code-block:: bash

       cd _build/emqx/rel/emqx
       emqx install
