# Hardware monigoring (grafana + prometheus + nodeexporter)

usage:
```
docker-compose up --d
docker-compose ps
docker-compose down
docker-compose down --v
```
testing:
```
sudo apt install sysbench
[cpu]
sysbench --num-threads=8 --test=cpu --cpu-max-prime=10000000 run
[ram]
sysbench --test=memory run
[hdd]
sysbench --test=fileio --file-total-size=16G prepare
sysbench --test=fileio --file-test-mode=seqwr run
sysbench --test=fileio cleanup

sudo apt install iperf3
iperf3 -c iperf.biznetnetworks.com -f M -t 30

dd if=/dev/zero of=/tmp/zero bs=1G count=24
stress-ng --vm-bytes $(awk '/MemAvailable/{printf "%d\n", $2 * 0.9;}' < /proc/meminfo)k --vm-keep -m 1
```
build:
```
docker build -f docker/Dockerfile.grafana -t grafana .
docker build -f docker/Dockerfile.prometheus -t prometheus .
```