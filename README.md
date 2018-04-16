# Build SONA from Disaggregated ONOS Repository

This project is intended for building SONA project from disaggregated ONOS repository.
Note that following tutorial is only for MAC OSX.

1. Install homebrew.
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Install repo using brew.
```
$ brew install repo
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

7. Run ONOS either in local or in remote.

8. Deploy SONA artifacts. Done!
```
$ onos-app $OC1 reinstall! sona-out/openstacknetworking.oar
$ onos-app $OC1 reinstall! sona-out/openstacknode.oar
$ onos-app $OC1 reinstall! sona-out/openstacknetworkingui.oar
```

