# AWS

## EC2 - Deploying Docker Project
1. ssh into EC2 instance
```bash
ssh -i your-key.pem ubuntu@<your-public-ip>
```

2. Setup
```bash
sudo apt update
sudo apt install -y ca-certificates curl gnupg lsb-release

sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker $USER

exit
ssh -i your-key.pem ubuntu@<your-public-ip>

docker --version
docker compose version
```

3. Upload project files
```
scp -i your-key.pem -r ./project-folder ubuntu@<your-ec2-ip>:~/project-folder
```

4. Navigate to project folder and start app
```
cd ~/project-folder
docker compose up -d --build
```
5. Edit Inbound Rules to expose app
   In the AWS Console:

   Go to EC2 > Instances > [Your instance] > Security Groups
  
   Edit Inbound Rules
   
   > Add rule: Custom TCP | Port 8000 | Source: 0.0.0.0/0
