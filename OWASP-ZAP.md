Connect to VM

sudo apt update && sudo apt upgrade -y

sudo apt install docker.io -y

sudo systemctl enable docker
sudo systemctl start docker

sudo usermod -aG docker $USER

exit
docker --version

docker run -d -p 3000:3000 bkimminich/juice-shop
docker ps
Open the Vulnerable Website

docker pull ghcr.io/zaproxy/zaproxy
docker images

docker run --rm ghcr.io/zaproxy/zaproxy zap-baseline.py -t http://<VM-IP>:3000

docker run --rm -v $(pwd):/zap/wrk ghcr.io/zaproxy/zaproxy zap-baseline.py -t http://<VM-IP>:3000 -r report.html

cd ~/zap-results
python3 -m http.server 8000

http://52.151.194.238:8000/zap-report.html
