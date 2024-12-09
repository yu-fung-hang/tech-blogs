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

## Get pod's log

```
kubectl describe pod your-pod-name
```

## /run/flannel/subnet.env: no such file or directory

```
FLANNEL_NETWORK=10.244.0.0/16
FLANNEL_SUBNET=10.244.0.1/24
FLANNEL_MTU=1450
FLANNEL_IPMASQ=true
```