## 404-base-miner

Enhanced 3D generator

### Hardware Requirements

To run this generator you will need a GPU with at least 24 GB of VRAM. It can work with GPUs from NVIDIA Blackwell family,
including Geforce 5090 RTX.

### Software Requirements

- latest docker package (we provide docker file in "docker" folder) or latest conda environment (we provide "conda_env.yml");
- NVIDIA GPU with cuda 12.8 support
- python 3.11

### Installation

- Docker (building & pushing to remote register):
```console
cd /docker
docker build --build-arg GITHUB_USER="" --build-arg GITHUB_TOKEN="" -t docker_name:docker-tag .
docker tag docker_name:docker-tag docker-register-path:docker-register-name
docker push docker-register-path:docker-register-name   
```
- Conda Env. (shell script will install everything you need to run the project):
```console
bash setup_env.sh
```
### How to run:
- Docker (run locally):
```commandline
docker run --gpus all -it docker_name:docker-tag bash

# outside docker
curl -X POST "http://0.0.0.0:10006/generate" -F "prompt_image_file=@/path/to/your/image.png" > model.ply
```
- Conda Env.:
```commandline
# start pm2 process
pm2 start generation.config.js

# view logs
pm2 logs

# send prompt image
curl -X POST "http://0.0.0.0:8094/generate" -F "prompt_image_file=@/path/to/your/image.png" > model.ply
```
