# Shell scripts

 
`$ docker image build --file /path/to/your/dockerfile --tag local:dockerfile-example .`
` `
`$ docker image build --tag local:dockerfile-example .`
` `
`$ docker image ls`
` `
`$ docker container ls`
` `
`$ docker container stop dockerfile-example $ docker container rm dockerfile-example nginx-version`
` `
`$ docker image pull alpine:latest `
` `
`Last resort shell access`
`$ docker container run -it --name <container-name> alpine /bin/sh`
` `
`$ docker container commit <container_name> <REPOSITORY>:<TAG>`
`$ docker container commit alpine-test local:broken-container`
` `
`$ docker image save -o <name_of_file.tar> <REPOSITORY>:<TAG>`
`$ docker image save -o broken-container.tar local:broken-container`
` `
` `
`ENV <key>=<value> ENV username=admin database=wordpress tableprefix=wp`

`docker image inspect <IMAGE_ID>`
` `

