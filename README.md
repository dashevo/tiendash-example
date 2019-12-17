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
apt update && apt upgrade -y && apt autoremove -y
curl -fsSL get.docker.com -o get-docker.sh && sh get-docker.sh && rm get-docker.sh
curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose

adduser strophy
usermod -aG sudo,docker strophy

fallocate -l 4G /swapfile
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile
echo '/swapfile none swap sw 0 0' >> /etc/fstab

echo 'vm.max_map_count = 262144' >> /etc/sysctl.conf
sysctl -p

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
