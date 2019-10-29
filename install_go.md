# Installing Go in Ubuntu 18.04

## Install

1. Use the Go downloads page as reference: https://golang.org/dl/
1. Fetch the Go Tarball
    ```shell script
    curl -O https://dl.google.com/go/go1.13.1.linux-amd64.tar.gz
    ```
1. Compare the checksum output with Go downloads page
    ```shell script
    sha256sum go1.13.1.linux-amd64.tar.gz
    ```
1. Extract the tarball
    ```shell script
    tar xvf go1.13.1.linux-amd64.tar.gz
    ```
1. Move the extracted folder to /usr/local
    ```shell script
    sudo chown -R root:root ./go
    sudo mv go /usr/local
    ```

## Configuration

1. Set the GOPATH
    ```shell script
    sudo nano ~/.profile
    ```

    Add the following at the end of the file
    ```text
    export GOPATH=$HOME/go
    export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
    ```

    Refresh the profile
    ```shell script
    source ~/.profile
    ```
