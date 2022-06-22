sudo apt install docker-compose
sudo usermod -a -G docker $USER
sudo systemctl restart docker

docker-compose up -d
docker-compose ps
docker-compose down
