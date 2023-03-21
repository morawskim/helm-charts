## Install chart

### mitmproxy

First create namespace `mitmproxy`, if not exists
`kubectl create namespace mitmproxy`

Install chart in namespace `mitmproxy` and release name set to `dev`
`helm install -n mitmproxy dev ./mitmproxy`

Upgrade chart in namespace `mitmproxy` and release `dev`
`helm upgrade -n mitmproxy dev ./mitmproxy/`

When you install this chart in cluster with ipv6 set parameter `allowGlobalIps` to value `true`:
`helm upgrade --set allowGlobalIps=true -n mitmproxy dev ./mitmproxy/`

To render chart template without applying changes run this command:
`helm upgrade --dry-run --debug --set allowGlobalIps=true -n mitmproxy dev ./mitmproxy/`

To uninstall release:
`helm uninstall -n mitmproxy dev`

Using via curl in other namespace:
`https_proxy=mitmproxy-<RELEASE_NAME>.<NAMESPACE>:8080 curl -k -X POST -H "Content-Type: application/json" -d '{"name": "John HTTPS"}' https://hookb.in/<ID>`

### mongodb-gui

See instruction for mitmproxy.

### redis-commander

To install with different redis host value:

`helm install --set redis=redis.othernamespace:6379 -n utils dev ./redis-commander/`

**WARNING** At the moment redis-commander will  not be able to connect to redis that listening on Ipv6 interface.

### adminer

See instruction for mitmproxy.

### phpMyAdmin

`helm install --set phpmyadmin_absolute_url=http://192.168.49.2/_phpmyadmin/ -n utils phpmyadmin ./phpmyadmin/`
