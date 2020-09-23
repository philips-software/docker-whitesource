[![Build Status](https://github.com/philips-software/docker-whitesource/workflows/build/badge.svg)](https://github.com/philips-software/docker-whitesource/actions/)
[![Slack](https://philips-software-slackin.now.sh/badge.svg)](https://philips-software-slackin.now.sh)

# Docker images

This repo will contain docker images with [Whitesource Agent](https://www.whitesourcesoftware.com/)

Current versions available:

```
.
├── 20
│   ├── docker
│   │   └── Dockerfile
│   ├── dotnetcore
│   │   └── Dockerfile
│   ├── java
│   │   └── Dockerfile
│   └── node
│       └── Dockerfile
```

## Usage

Images can be found on [https://hub.docker.com/r/philipssoftware/whitesource/](https://hub.docker.com/r/philipssoftware/whitesource/).

``` bash
docker run -v $PWD:/code philipssoftware/whitesource:20 java -jar /app/wss-unified-agent.jar -d /code -c /code/whitesource.config
```

In order to analyse a project use the following structure.

_Replace all <your-xxxxx> variables with your own variables_

## Content

The images obviously contain whitesource and java8, but also two other files:

- `REPO`
- `TAGS`

### REPO

This file has a url to the REPO with specific commit-sha of the build.
Example: 

```
$ docker run philipssoftware/whitesource:20 cat REPO
https://github.com/philips-software/docker-whitesource/tree/facb2271e5a563e5d6f65ca3f475cefac37b8b6c
```

### TAGS

This contains all the similar tags at the point of creation. 

```
$ docker run philipssoftware/whitesource:20 cat TAGS
whitesource whitesource:20 whitesource:20.5 whitesource:20.5.2
```

You can use this to pin down a version of the container from an existing development build for production. When using `whitesource:20` for development. This ensures that you've got all security updates in your build. If you want to pin the version of your image down for production, you can use this file inside of the container to look for the most specific tag, the last one.

## Simple Tags

### whitesource
- `whitesource`, `whitesource:20`, `whitesource:20.6`, `whitesource:20.6.2` [20/java/Dockerfile](20/java/Dockerfile)

### whitesource with node
- `whitesource:node`, `whitesource:20-node`, `whitesource:20.6-node`, `whitesource:20.6.2-node` [20/node/Dockerfile](20/node/Dockerfile)

### whitesource with dotnetcore
- `whitesource:dotnetcore`, `whitesource:20-dotnetcore`, `whitesource:20-dotnetcore-3`, `whitesource:20.6-dotnetcore`, `whitesource:20.6-dotnetcore-3.0`, `whitesource:20.6.2-dotnetcore`, `whitesource:20.6.2-dotnetcore-3.0.101` [20/dotnetcore/Dockerfile](20/dotnetcore/Dockerfile)

### whitesource with docker
- `whitesource:docker`, `whitesource:20-docker`, `whitesource:20.6-docker`, `whitesource:20.6.2-docker` [20/docker/Dockerfile](20/docker/Dockerfile)


## Why

> Why do we have our own docker image definitions?

We often need some tools in a container for checking some things. F.e. [jq](https://stedolan.github.io/jq/), [aws-cli](https://aws.amazon.com/cli/) and [curl](https://curl.haxx.se/).
We can install this every time we need a container, but having this baked into a container seems a better approach.

That's why we want our own docker file definitions.

## Known Issues

Currently this image only has java. Running a project with `yarn` or `npm` will not work yet.

## Issues

- If you have an issue: report it on the [issue tracker](https://github.com/philips-software/docker-whitesource/issues)

## Author

- Jeroen Knoops <jeroen.knoops@philips.com>
- Sanda Contiu <sanda.contiu@philips.com>

## License

License is MIT. See [LICENSE file](LICENSE.md)

## Contributors

[//]: contributor-faces
<a href="https://github.com/JeroenKnoops"><img src="https://avatars1.githubusercontent.com/u/10019?v=4" title="JeroenKnoops" width="80" height="80"></a>
<a href="https://github.com/bartgolsteijn"><img src="https://avatars0.githubusercontent.com/u/3263880?v=4" title="bartgolsteijn" width="80" height="80"></a>
<a href="https://github.com/npalm"><img src="https://avatars2.githubusercontent.com/u/11609620?v=4" title="npalm" width="80" height="80"></a>
<a href="https://github.com/timovandeput"><img src="https://avatars3.githubusercontent.com/u/5458560?v=4" title="timovandeput" width="80" height="80"></a>
<a href="https://github.com/apps/dependabot"><img src="https://avatars0.githubusercontent.com/in/29110?v=4" title="dependabot[bot]" width="80" height="80"></a>

[//]: contributor-faces

## Philips Forest

This module is part of the Philips Forest.

```
                                                     ___                   _
                                                    / __\__  _ __ ___  ___| |_
                                                   / _\/ _ \| '__/ _ \/ __| __|
                                                  / / | (_) | | |  __/\__ \ |_
                                                  \/   \___/|_|  \___||___/\__|  

                                                                 Infrastructure
```

Talk to the forestkeepers in the `docker-images`-channel on Slack.

[![Slack](https://philips-software-slackin.now.sh/badge.svg)](https://philips-software-slackin.now.sh)
