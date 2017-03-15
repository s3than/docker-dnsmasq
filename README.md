# docker-dnsmasq

dnsmasq in a docker container, configurable via a [simple web UI](https://github.com/s3than/webproc)

<!--[![Docker Pulls](https://img.shields.io/docker/pulls/jpillora/dnsmasq.svg)][dockerhub]
[![Image Size](https://images.microbadger.com/badges/image/jpillora/dnsmasq.svg)][dockerhub]-->

### Usage

1. Create a [`data/dnsmasq.conf`](http://oss.segetech.com/intra/srv/dnsmasq.conf) file on the Docker host

	``` ini
	#dnsmasq config, for a complete example, see:
	#  https://github.com/s3than/go-dnsmasq
	192.168.0.1 db1.db.local
	192.168.0.2 *.db.local
	```

1. Run the container

	```
	$ docker run \
		--name dnsmasq \
		-d \
		-p 53:53/udp \
		-p 5380:5380 \
		-v data/dnsmasq.conf:/data/dnsmasq.conf \
		--log-opt "max-size=100m" \
		-e "USER=foo" \
		-e "PASS=bar" \
		s3than/dnsmasq
	```

1. Visit `http://<docker-host>:5380`, authenticate with `foo/bar`

	<!--<img width="726" alt="screen shot 2016-10-02 at 10 27 46 pm" src="https://cloud.githubusercontent.com/assets/633843/19020264/c6d8eee8-88ef-11e6-9eee-c09aa07cad62.png">-->

