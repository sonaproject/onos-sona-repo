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

5. Clone all repositories (ONOS + SONA + prebuilt bucklet).
```
$ repo sync
```

6. Build SONA project separately. Following cmd will only build SONA project with ONOS dependencies.
```
$ buck build onos
```

7. Run ONOS either in local or in remote.

8. Deploy SONA artifacts. Done!
```
$ onos-app $OC1 reinstall! buck-out/gen/apps/openstacknetworking/onos-apps-openstacknetworking-oar/app.oar
$ onos-app $OC1 reinstall! buck-out/gen/apps/openstacknode/onos-apps-openstacknode-oar/app.oar
```

