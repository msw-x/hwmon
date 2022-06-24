sudo apt install docker-compose
sudo usermod -a -G docker $USER

git clone git://mswo.ru/msw/hwmon

docker-compose up --detach
docker-compose ps
docker-compose down
docker-compose down --volumes

docker ps -a
docker ps --size
docker system df
docker images
docker image rm NAME
docker container ls -a
docker container rm ID/NAME


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
