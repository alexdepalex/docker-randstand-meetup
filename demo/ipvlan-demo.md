# ipvlan

## L3 mode

### Set up two network name spaces

```
ip netns add ns0
ip netns add ns1
ip link add link eno16777736 ipvl0 type ipvlan mode l3
ip link add link eno16777736 ipvl1 type ipvlan mode l3
ip link set dev ipvl0 netns ns0
ip link set dev ipvl1 netns ns1
```

```
ip netns exec ns0 bash
ip link set dev ipvl0 up
ip link set dev lo up
ip addr add 127.0.0.1 dev lo
ip addr add 10.10.0.10/8 dev ipvl0
ip route add default dev ipvl0
```

```
ip netns exec ns1 bash
ip link set dev ipvl1 up
ip link set dev lo up
ip addr add 127.0.0.1 dev lo
ip addr add 10.10.0.11/8 dev ipvl1
ip route add default dev ipvl1
```
