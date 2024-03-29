# HLP-docker
Docker environment for HLP projects.

## Dockerfile.server (run vscode in web browser)
### Build the docker image
`docker build -f Dockerfile.server -t hlp-dev .`

Requires `docker-entrypoint.sh` in current directory.

### Run the docker image

```
docker run -p 8443:8443 -e LOCAL_USER_ID=`id -u $USER` -v $(pwd)/data:/home/dockeruser/data -v $(pwd)/code:/home/dockeruser/code -dt --rm hlp-dev
```

Now VS Code is available from your browser at [localhost:8443](https://localhost:8443).

The `data` dir contains the vscode settings, extensions & session.

### Sharing additional directories

Share additional directories with your Docker vscode instance by adding the following to the `docker run` command:
```
-v $(pwd)/directory:/home/directory
```

### Dependencies included

- fsharp via the [official fsharp docker image](https://hub.docker.com/_/fsharp)
- vscode server 1.1156-vsc1.33.1 - check https://github.com/cdr/code-server/releases/latest for lastest version.
- [nvm](https://github.com/nvm-sh/nvm) Node version manager
- [yarn](https://yarnpkg.com/lang/en/) Yarn package manager
