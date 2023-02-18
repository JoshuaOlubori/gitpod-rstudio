# gitpod-rstudio
Gitpod environment for working with RStudio Server

https://www.drdataking.com/post/rstudio-server-on-ubuntu-through-windows-subsystem-for-linux-wsl2/


Use the following commands to upgrade Ubuntu packages

```
sudo apt-get update
sudo apt-get upgrade -y
```
add credentials to your repository list for Getting the Latest R

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
sudo add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu focal-cran40/'
```

The following command is to install the most recent R and some necessary dependencies
```
sudo apt install -y r-base r-base-core r-recommended r-base-dev gdebi-core build-essential libcurl4-gnutls-dev libxml2-dev libssl-dev
```

Install RStudio Server using the following commands
```
wget https://rstudio.org/download/latest/stable/server/bionic/rstudio-server-latest-amd64.deb
sudo gdebi -y rstudio-server-latest-amd64.deb
```

Launch the RStudio Server
```
sudo rstudio-server start
```

Add user (for RStudio) ABCDE with passaord ABCDE (feel free to change as desired)

```
sudo useradd   -s /bin/bash -p $(echo ABCDE | openssl passwd -1 -stdin) ABCDE
```

Open RStudio - from the Ports tab open the URL listed for port 8787. RStudio launches in a new browser window. Login with username ABCDE and password ABCDE.

## Note: Remove/Uninstall

If you want to stop and remove/uninstall the server, you may do the following:

```
# To stop the server
sudo rstudio-server stop

# To remove the server
sudo apt-get remove rstudio-server -y
``` 