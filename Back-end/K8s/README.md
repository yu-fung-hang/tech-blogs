# K8s

## Error 1: /proc/sys/net/bridge/bridge-nf-call-iptables does not exist

```
modprobe br_netfilter
```

## Check Kubelet log

```
journalctl -xefu kubelet
```

## Get nodes' info

```
kubectl get nodes
```