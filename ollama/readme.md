readme.md



sudo pkill -f ollama
sudo pkill -9 ollama
sudo pkill -9 -f ollama

sudo systemctl stop ollama



~/.ollama/models → EMPTY
/usr/share/ollama/.ollama/models → CLEAN

cd ~/.ollama/models/
rm -rf blobs
rm -rf manifests

ls -lah /usr/share/ollama/.ollama/models
sudo rm -rf /usr/share/ollama/.ollama/models/blobs
sudo rm -rf /usr/share/ollama/.ollama/models/manifests


sudo systemctl start ollama
systemctl status ollama
