## Elixr Testnet1 setup guide
<p align="center"><img height="150" height="auto" src="https://user-images.githubusercontent.com/63885192/218285980-9125f397-4ee0-467a-814a-cf1eb29512e3.jpg"></p>

### Update & Install Docker
```
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

```
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```
sudo apt-get update
```

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```
wget https://testnet-1-files.elixir.finance/Dockerfile
```

### input your metamask adreess and your private key, recommendation to create a new wallet.
```
nano Dockerfile
```

```
docker build . -f Dockerfile -t elixir-validator
```

```
docker run -d --restart unless-stopped --name ev elixir-validator
```

now visit https://metrics.elixir.finance/ to see your address
Press CTRL f, then paste the new metamask address into the search field, then press enter. if it doesn't appear wait a few minutes, you can also search by IP which you can retrieve from your VPS.
