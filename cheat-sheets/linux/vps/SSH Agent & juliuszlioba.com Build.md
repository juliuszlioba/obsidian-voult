SSH key add
```bash
eval `ssh-agent`
ssh-add ~/.ssh/id_vps
```

juliuszlioba.com Build

```bash
cd ./projects/juliuszlioba-astro

eval `ssh-agent`

ssh-add ~/.ssh/id_vps

git pull

docker compose build

docker compose up -d
```