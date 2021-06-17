# romeio-protoactor-dev-container
Docker container for development of protoactor-go projects


Build local image from dockerfile (typically, tag will be "latest"):
`docker build -t romeio/romeio-dev:<tag> .`
If apt-update error InRelease is not valid yet:
`wsl -d docker-desktop hwclock -s`
`wsl -d docker-desktop-data sudo hwclock -s`
Then run the build again.

If image built with different name, rename/retag it before pushing:
`docker tag <local-image>:<tag> romeio/romeio-dev:<tag>`

Push local image to Docker Hub repository (typically, tag will be "latest")
`docker push romeio/romeio-dev:<tag>`

Run locally w/ interactive shell (typically, tag will be "latest"):
`docker run -it  -p 2379:2379 -p 2380:2380 -v gopathvol:/go romeio/romeio-dev:<tag> /usr/bin/zsh`
If you haven't created the docker volume, leave out the -v options. Note that if the local folder for the volume (if mapped) already exists, the contents of the directory in the container will NOT be copied to the volume, so your contents on your local filesystem is what will show up in the container.
