## awesome 4.2 deb package for Debian Buster

This is the Dockerfile that can be used to build the deb package for *Debian Buster*.

To get a `deb` file just execute next commands:

```
cd awesome
docker build -t awesome:v1 .
DEB_FILE=$(docker run awesome:v1  bash -c 'ls -1 /root/awesome*.deb' )
docker cp $(docker ps -a -n=1 -q):${DEB_FILE} .
```

Then, to install, execute

```
sudo dpkg -i ./$(basename "${DEB_FILE}")
sudo apt-get -f install  # To install missing dependencies (dpkg doesn't install any dependencies)
```

