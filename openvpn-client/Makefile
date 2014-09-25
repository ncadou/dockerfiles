IMAGE ?= ncadou/openvpn-client
CONTAINER ?= openvpn-client
PROVIDER ?= pia
CONFIG ?= US East.ovpn
USERNAME ?= username
PASSWORD ?= password

ifdef INSTANCE
CONTAINER := $(CONTAINER)-$(INSTANCE)
endif

HOSTNAME ?= $(CONTAINER)

OPTIONS = -h $(HOSTNAME) \
	  --cap-add=MKNOD \
	  --cap-add=NET_ADMIN \
	  --device=/dev/net/tun \
	  -e "OPENVPN_USERNAME=$(USERNAME)" \
	  -e "OPENVPN_PASSWORD=$(PASSWORD)"

.PHONY: build diff logs restart rm rmi shell start stop tail

diff logs restart start stop:
	docker $@ $(CONTAINER)

build: .build
.build: Dockerfile
	docker build --rm -t $(IMAGE) .
	touch .build

rmi:
	docker rmi $(IMAGE)
	-rm -f .build

shell: build Makefile
	docker run --rm -i -t $(OPTIONS) $(IMAGE) bash

ls: list
list: build Makefile
	docker run --rm -i -t --entrypoint ls $(OPTIONS) $(IMAGE) \
		-l /usr/local/share/openvpn/providers/$(PROVIDER)

run: .run
.run: build Makefile
	docker run -d --name $(CONTAINER) $(OPTIONS) $(IMAGE) \
		$(PROVIDER) '$(CONFIG)'
	touch .run

rm:
	docker rm $(CONTAINER)
	-rm -f .run

tail:
	docker logs -f $(CONTAINER)
