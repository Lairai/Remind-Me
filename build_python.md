# Building Python 3.8.x in Ubuntu 18.04

1. Update the package list and upgrade if necessary.
     ```shell script
     sudo apt update
     sudo apt upgrade -y
     ```
1. Install wget and the default GCC toolchain to build Python source code.
    - [build-essential](https://packages.ubuntu.com/bionic/build-essential)
    - [wget](https://packages.ubuntu.com/bionic/wget)
    ```shell script
    sudo apt install build-essential wget
    ```
1. Install the following dev packages to use the standard packages in Python
    - [zlib1g-dev](https://packages.ubuntu.com/bionic/zlib1g-dev)
    - [libbz2-dev](https://packages.ubuntu.com/bionic/libbz2-dev)
    - [liblzma-dev](https://packages.ubuntu.com/bionic/liblzma-dev)
    - [libncurses5-dev](https://packages.ubuntu.com/bionic/libncurses5-dev)
    - [libncursesw5-dev](https://packages.ubuntu.com/bionic/libncursesw5-dev)
    - [libgdbm-dev](https://packages.ubuntu.com/bionic/libgdbm-dev)
    - [libnss3-dev](https://packages.ubuntu.com/bionic/libnss3-dev)
    - [libssl-dev](https://packages.ubuntu.com/bionic/libssl-dev)
    - [libreadline-dev](https://packages.ubuntu.com/bionic/libreadline-dev)
    - [libffi-dev](https://packages.ubuntu.com/bionic/libffi-dev)
    - [libsqlite3-dev](https://packages.ubuntu.com/bionic/libsqlite3-dev)
    - [libdb5.3-dev](https://packages.ubuntu.com/bionic/libdb5.3-dev)
    - [libexpat1-dev](https://packages.ubuntu.com/bionic/libexpat1-dev)
    - [uuid-dev](https://packages.ubuntu.com/bionic/uuid-dev)
    ```shell script
   sudo apt install zlib1g-dev libbz2-dev liblzma-dev libncurses5-dev libncursesw5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev libdb5.3-dev libexpat1-dev uuid-dev
   ```
1. Download the latest 3.8.x release from [Python Downloads page](https://www.python.org/downloads/).
    ```shell script
    wget https://www.python.org/ftp/python/3.8.1/Python-3.8.1.tar.xz
    ```
1. Extract the tar ball
    ```shell script
    tar -xf Python-3.8.1.tar.xz
    ```
1. Run the configure script to make sure all of the dependencies on your system are present. For Python packages such as mod_wsgi, add the option --enable-shared.
    ```shell script
    cd Python-3.8.1
    ./configure --enable-optimizations
    ```
1. Start the Python build process. The j parameter specifies the number of CPU cores. To find your core count, run the nproc command.
    ```shell script
    sudo make -j $(nproc)
    ```
1. Install the Python Binaries. Do not use install as it will override the default Python binaries.
    ```shell script
    sudo make altinstall
    ```
1. [Optional] If you used --enabled-shared option, you may need to create a symbolic link to /usr/lib.
    ```shell script
    sudo ln -s /usr/local/lib/libpython3.8m.so.1.0 /usr/lib/libpython3.8m.so.1.0
    ```
1. Verify that Python 3.8.x is installed.
    ```shell script
    python3.8 --version
    ```
