# Build SONA from Disaggregated ONOS Repository

This project is intended for building SONA project from disaggregated ONOS repository.
Prerequisite for the build machine is JDK 8.x (OracleJDK or OpenJDK) and Python 2.x.

1. Install repo.

In MacOSX:
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
$ brew install repo
```

In Linux:
```
$ mkdir -p ~/bin
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
$ chmod a+x ~/bin/repo
$ sudo mv ~/bin/repo /bin/repo
```

2. Install software dependencies.

In RHEL (CentOS):
```
$ sudo yum install -y zip unzip bzip2
```

In Debian (Ubuntu):
```
$ sudo apt-get install -y zip unzip bzip2
```


3. Create a directory for placing ONOS and SONA source code.
```
$ mkdir -p ~/git/sona-repo
```

4. Initialize repo.
```
$ cd ~/git/sona-repo
$ repo init -u https://github.com/sonaproject/onos-sona-repo.git
```

5. Clone all repositories (Stable branch of ONOS + Master branch of ONOS + SONA buck tool set).
```
$ repo sync
```

6. Run build.sh script to build latest version of SONA apps against stable version of ONOS.
Note that the resulting SONA artifacts will be located under sona-out directory.
```
$ ./build.sh
```

7. [Optional] Run verify.sh script to execute unit tests for SONA apps.
```
$ ./verify.sh
```

8. Run ONOS either in local or in remote.

9. Deploy SONA artifacts to ONOS. Done!
```
$ onos-app $ONOS_IP reinstall! sona-out/openstacknode.oar
$ onos-app $ONOS_IP reinstall! sona-out/openstacknetworking.oar
$ onos-app $ONOS_IP reinstall! sona-out/openstacknetworkingui.oar
```

10. Wipe out workspace.
```
$ ./clean.sh
```
