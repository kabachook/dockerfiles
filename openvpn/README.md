# Basic openvpn in docker

* Generate config 
```sh
docker-compose run --rm openvpn ovpn_genconfig -u udp://VPN.SERVERNAME.COM
```
* Init PKI (you can specify tls-ciphers or encryption)
```sh
docker-compose run --rm openvpn ovpn_initpki
```
* Start container 
```sh
docker-compose up -d openvpn
```
* Generate client
```sh
export CLIENTNAME="your_client_name"
# with a passphrase (recommended)
docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME
# without a passphrase (not recommended)
docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME nopass
```
* Retrieve config
```sh
docker-compose run --rm openvpn ovpn_getclient $CLIENTNAME > $CLIENTNAME.ovpn
```

> By default uses 4096 RSA key size (editable in `EASYRSA_KEY_SIZE=4096`)
>
> Supports elliptic curves encryption (see [here](https://github.com/kylemanna/docker-openvpn/issues/1))
>
> [Additional documentation](https://github.com/kylemanna/docker-openvpn/tree/master/docs)

## Thanks @kylemanna for such a nice docker image!