# Overwrite previous DockerDesktop configuration

If DockerDesktop is already installed and being used, then existing users of may have already updated a setting, which in turn will have been written to the relevant config file, for example the `settings-store.json` (or `settings.json` for Docker Desktop versions 4.34 and earlier) or `daemon.json`. 

In these instances, the user's preferences are respected and the values aren't altered. This can be incredibly frustrating when trying to reassign where the docker engine is going to look for its vm disk imgs. Especially if the old user profile is deleted, the docker enginer will be attempting to read a non-existant directory. 

## settings.json and settings-store.json 

```zsh
 #settings-store.json location
/Library/Group\ Containers/com.docker.docker/settings-store.json

 #settings-store.json location
/Library/Group\ Containers/com.docker.docker/settings.json
```
Alternatively you can install DockerDesktop, but sepcify the user profile (note: this required admin privileges)

```zsh
$ /Applications/Docker.app/Contents/MacOS/install --user=<userid>
```
To avoid this whole step, you can delete the `settings-store.json` file (or `settings.json` for Docker Desktop versions 4.34 and earlier) left behind from any previous installations before launching the application.

[source](https://docs.docker.com/security/for-admins/hardened-desktop/settings-management/configure-json-file/#step-two-configure-the-settings-you-want-to-lock-in)
