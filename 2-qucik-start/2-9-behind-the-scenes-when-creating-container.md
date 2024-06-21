<!-- This md file is originally converted from onenote -->

# [創建容器時背後發生了什麼](https://dockertips.readthedocs.io/en/latest/container-quickstart/docker-container-run-happend.html)

2023年2月12日
下午 03:13

## Contents [[↑](#創建容器時背後發生了什麼)]

- [創建容器時背後發生了什麼](#創建容器時背後發生了什麼)
  - [Contents \[↑\]](#contents-)
    - [`docker container run` 背後發生了什麼？ \[↑\]](#docker-container-run-背後發生了什麼-)

### `docker container run` 背後發生了什麼？ [[↑](#創建容器時背後發生了什麼)]

- 先運行一個 container 起來
  - `$ docker container run -d --publish 80:80 --name webhost nginx`
  - 命令解釋
    - `$ docker container run -d --publish 80:80` **`--name <給容器起一個名字>`** `<image_name>` **`<執行的命令>`**
      - 不指定 `<容器的名字>`, 系統會隨機分配
      - 不指定 `<執行的命令>`, 則會執行默認的命令 (defined in the Dockerfile)
        - 後麵再解釋什麼是 **默認的命令**
      - `--publish` 是網路相關的 topic, 後面再解釋

- 背後運行的步驟
  1. 準備 image
     - 在本地查找是否有 nginx 這個 image 鏡像，但是沒有找到
     - 去遠程的 image registry 查找 nginx 鏡像 (默認的 registry 是 Docker Hub)
     - 下載最新版本的 nginx 鏡像 (默認使用 nginx:latest)
  2. 創建 container (在 image read-only 的基礎上添加一層 read-write layer)
     - 基於 nginx 鏡像來創建一個新的容器，並且準備運行
  3. 網路配置
     - docker engine 會為這個容器分配一個虛擬 IP 地址
     - 在宿主機上打開 80 端口並把容器的 80 端口轉發到宿主機上
  4. 啓動容器
     - 啓動容器，運行指定的命令（這裏是一個 shell 腳本去啓動 nginx）
