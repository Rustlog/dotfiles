.PHONY: all fedora-dev ubuntu-server fedora-server

all:
	fedora-dev ubuntu-server fedora-server

fedora-dev:
	podman build -t fedora-dev:latest -f dockerfiles/Dockerfile.fedora-dev build-context/
	podman run -dt --init --init-path /usr/bin/tini --name fedora-dev --hostname fedora-container -p 8026:22 -p 6084:80 -p 6447:443 localhost/fedora-dev:latest /usr/bin/tini -- /usr/bin/bash
	podman exec -it fedora-dev bash

ubuntu-storage:
	podman build -t ubuntu-storage:latest -f dockerfiles/Dockerfile.ubuntu-storage build-context/
	podman run -dt --name ubuntu-storage --hostname ubuntu-storage-container -p 8028:22 -p 6088:80 -p 6449:443 localhost/ubuntu-storage:latest /usr/bin/tini -- /usr/bin/tini -- /usr/bin/bash

fedora-server:
	podman build -t fedora-server:latest -f dockerfiles/Dockerfile.fedora-server build-context/
	podman run -dt --name fedora-server --hostname fedora-server-container -p 8022:22 -p 6080:80 -p 6443:443 localhost/fedora-server:latest /usr/bin/tini -- /usr/bin/tini -- /usr/bin/bash

