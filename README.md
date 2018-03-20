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

5. Clone all repositories (ONOS + SONA Apps + SONA buck tool set).
```
$ repo sync
```

6. Build BUCK plugins. 
```
$ buck build //tools/build/buck-plugin:onos
```

7. Copy the buck plugin under bin directory.
```
$ mkdir -p bin/plugins && cp buck-out/gen/tools/build/buck-plugin/onos.jar bin/plugins
```

8. Build SONA project separately. Following cmd will only build SONA project with ONOS dependencies.
```
$ buck build onos
```

9. Run ONOS either in local or in remote.

10. Deploy SONA artifacts. Done!
```
$ onos-app $OC1 reinstall! buck-out/gen/apps/openstacknetworking/onos-apps-openstacknetworking-oar/app.oar
$ onos-app $OC1 reinstall! buck-out/gen/apps/openstacknode/onos-apps-openstacknode-oar/app.oar
$ onos-app $OC1 reinstall! buck-out/gen/apps/openstacknetworkingui/onos-apps-openstacknetworkingui-oar/app.oar
```

