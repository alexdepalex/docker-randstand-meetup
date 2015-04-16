# flannel

```
etcdctl ls /coreos.com/network --recursive
```

## Terminal 1

```
ssh core@192.168.12.100
```

```
docker run -t -i busybox /bin/sh -c 'ifconfig eth0 && nc -l -p 80'
```

## Terminal 2

```
ssh core@192.168.12.101
```

```
docker run -t -i busybox /bin/sh -c 'nc <eth0-ip>:80'
```
