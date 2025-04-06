# DDNS

## ansible

```shell
ansible-playbook ddns.yaml
```

## dynv6.com

```shell
dd_ipv4=$(curl -s ip4only.me/api/ | awk -F, '{print $2}')
curl -v "https://dynv6.com/api/update?hostname=$hostname&token=$token&ipv4=$dd_ipv4"

dd_ipv6=$(curl -s ip6only.me/api/ | awk -F, '{print $2}')
curl http://dynv6.com/api/update?hostname=$hostname&token=$token&ipv6=$dd_ipv6&ipv6prefix=$ip6lanprefix

```

