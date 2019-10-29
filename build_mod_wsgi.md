# Building mod_wsgi 4.6.x for Apache 2.4.x in Ubuntu 18.04

This instructions assumes that you installed Python3.8 as instructed [here](build_python.md). 

1. Update the package list and upgrade if necessary.
     ```shell script
     sudo apt update
     sudo apt upgrade -y
     ```
1. Install necessary Apache 2 dev tools to build third-party modules.
    - [apache2-dev](https://packages.ubuntu.com/bionic/apache2-dev)
    ```shell script
    sudo apt install apache2-dev
    ```
1. Download the latest 4.6.x mod_wsgi release from [mod_wsgi releases](https://github.com/GrahamDumpleton/mod_wsgi/releases).
    ```shell script
    wget https://github.com/GrahamDumpleton/mod_wsgi/archive/4.6.8.tar.gz
    ```
1. Extract the tar ball
    ```shell script
    tar xvfz 4.6.8.tar.xz
    ```
1. Run the configure script to make sure all of the dependencies on your system are present.
    ```shell script
    cd mod_wsgi-4.6.8/
    ./configure --with-python=/usr/local/bin/python3.8
    ```
1. Start the build process.
    ```shell script
    sudo make
    ```
1. Install the module into the default Apache folder i.e. /usr/lib/apache2/modules/
    ```shell script
    sudo make install
    ```
1. Add module to mods-available Apache 2 folder.
    ```shell script
    sudo nano /etc/apache2/mods-available/wsgi.load
    ```
    Then, add the following line:
    ```text
    LoadModule wsgi_module /usr/lib/apache2/modules/mod_wsgi.so
    ```
1. Enable mod_wsgi module and restart the Apache 2 server.
    ```shell script
    sudo a2enmod wsgi
    sudo systemctl restart apache2
    ```
1. Check whether wsgi_module is shown as loaded.
    ```shell script
    apachectl -M
    ```
