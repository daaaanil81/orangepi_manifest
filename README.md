# orangepi_manifest

Manifest for Camera WebRTC Project

Support (https://github.com/linux-sunxi/meta-sunxi.git):
1. orange-pi-one
2. orange-pi-pc-plus
3. orange-pi-pc
4. orange-pi-zero-plus2-h3
5. orange-pi-zero-plus2
6. orange-pi-zero

## Install Google Repo
```bash
mkdir ~/bin
PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo-1 > ~/bin/repo
chmod a+x ~/bin/repo
```

## Setup docker
```bash
docker pull daaaanil81/camera_container # Download container
docker run -it --name camera_container daaaanil81/camera_container # Start container
docker commit camera_container daaaanil81/camera_container # Save container
docker rm camera_container # Delete last starting container
docker push daaaanil81/camera_container # Push container to server
```

## Fetching Source
```bash
mkdir -p CameraProject
cd CameraProject
repo init -u https://github.com/daaaanil81/orangepi_manifest
repo sync
```

## Building Project
```bash
cd CameraProject
source scripts/build.sh
```

## Flash to sdcard
```bash
cd CameraProject/build/tmp/deploy/images/<MACHINE>
sudo dd if=core-image-minimal-<MACHINE>.sunxi-sdimg of=<DEVICE> bs=1M
dd if=u-boot-sunxi-with-spl.bin of=<DEVICE> bs=1024 seek=8 conv=notrunc
```
