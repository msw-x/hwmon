sudo apt install docker-compose
sudo usermod -a -G docker $USER
sudo systemctl restart docker

docker-compose up --detach
docker-compose ps
docker-compose down
docker-compose down --volumes
