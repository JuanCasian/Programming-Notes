# Docker configuration for container that runs excercises

## installing docker

1. Using homebrew run:
	- `brew install docker-machine`
	- `brew install docker`
2. Create the docker-machine
	- `docker-machine create <name> -d "virtualbox"`
3. Share your local folder with virtual machine folder
	- `VBoxManage sharedfolder add <vmName/id> --name <sharedFolderName> --hostpath <folder> --automount`
4. Connect to the docker-machine
	- `docker-machine env <vmName>`
	- `eval $(docker-machine env <vmName>)`
5. Create docker container
	- `docker run  --name="webdev" -ti -v /LocalShare:/Shared -p 80:80 ubuntu`