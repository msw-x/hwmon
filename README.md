sudo apt install docker-compose
sudo usermod -a -G docker $USER

docker-compose up -d
docker-compose ps
