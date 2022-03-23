## Install chart

### mitmproxy

First create namespace `mitmproxy`, if not exists
`kubectl create namespace mitmproxy`

Install chart in namespace `mitmproxy` and release name set to `dev`
`helm install -n mitmproxy dev ./mitmproxy`

To uninstall release:
`helm uninstall -n mitmproxy dev`

Using via curl in other namespace:
`https_proxy=mitmproxy-<RELEASE_NAME>.<NAMESPACE>:8080 curl -k -X POST -H "Content-Type: application/json" -d '{"name": "John HTTPS"}' https://hookb.in/<ID>`
