.PHONY: all fedora-dev ubuntu-server fedora-server

all:
	fedora-dev ubuntu-server fedora-server

fedora-dev:
	mkdir -p build-context
	podman build -t fedora-dev:latest -f dockerfiles/fedora-dev.dockerfile ./
	podman run -dt --name fedora-dev --hostname fedora-dev-container -p 8026:22 -p 6084:80 -p 6447:443 localhost/fedora-dev:latest /usr/bin/tini -- /usr/bin/bash
	podman exec -it fedora-dev bash

fedora-server:
	podman build -t fedora-server:latest -f dockerfiles/fedora-server.dockerfile ./
	podman run -dt --name fedora-server --hostname fedora-server-container -p 8022:22 -p 6080:80 -p 6443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 localhost/fedora-server:latest /usr/bin/tini -- /usr/bin/bash

ubuntu-server:
	podman build -t ubuntu-server:latest -f dockerfiles/ubuntu-server.dockerfile ./
	podman run -dt --name ubuntu-server --hostname ubuntu-server-container -p 8022:22 -p 6080:80 -p 6443:443 -p 3306:3306 -p 5432:5432 -p 6379:6379 localhost/ubuntu-server:latest /usr/bin/tini -- /usr/bin/bash

ubuntu-storage:
	podman build -t ubuntu-storage:latest -f dockerfiles/ubuntu-storage.dockerfile ./
	podman run -dt --init --name ubuntu-storage --hostname ubuntu-storage-container -p 8028:22 -p 6088:80 -p 6449:443 localhost/ubuntu-storage:latest /usr/bin/tini -- /usr/bin/bash

