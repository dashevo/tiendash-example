# TienDash Example Store

> Example Dash store setup w/Magento and BTCPayserver

## Table of Contents
- [Install](#install)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Prerequisites

- [Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
- nginx
- a domain to use for the site
- optional: SSL certificate (outside scope of this README, use certbot for free certificates)

```sh
apt update
apt install -y nginx-light
```

## Usage

```sh
git clone https://github.com/strophy/btcpayserver-docker
cd btcpayserver-docker
export BTCPAY_HOST="104.238.180.251.vultr.com"
export NBITCOIN_NETWORK="mainnet"
export BTCPAYGEN_CRYPTO1="dash"
export BTCPAYGEN_REVERSEPROXY="nginx"
export BTCPAY_ENABLE_SSH=false
export REVERSEPROXY_HTTP_PORT=8080
export REVERSEPROXY_HTTPS_PORT=8443
export BTCPAYGEN_ADDITIONAL_FRAGMENTS="opt-add-magento.custom"
export BTCPAYGEN_EXCLUDE_FRAGMENTS="nginx-https;opt-add-tor"
. ./btcpay-setup.sh -i

```

## License

[ISC](LICENSE)
