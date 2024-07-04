# 本章 Docker 命令 - Cheat Sheet

## Contents [[↑](#本章-docker-命令---cheat-sheet)]

- [本章 Docker 命令 - Cheat Sheet](#本章-docker-命令---cheat-sheet)
  - [Contents \[↑\]](#contents-)
    - [鏡像管理 \[↑\]](#鏡像管理-)
    - [鏡像構建 \[↑\]](#鏡像構建-)
    - [容器管理 \[↑\]](#容器管理-)
    - [Docker Hub \[↑\]](#docker-hub-)
    - [其他重要概念 \[↑\]](#其他重要概念-)
    - [Cheat sheet \[↑\]](#cheat-sheet-)

以下是本章所使用的 Docker 命令，並根據其功能分類，同時指出了命令出現的章節:

### 鏡像管理 [[↑](#本章-docker-命令---cheat-sheet)]

- `docker image pull <image_name>:<tag>`  
  - 功能：從 registry 拉取 Docker 鏡像。
  - 說明：
    - `<image_name>` 是鏡像的名稱。
    - `<tag>` 是可選的，用於指定鏡像版本，默認為 `latest`。
  - 出現章節：[4-2 鏡像的獲取方式](./4-2-methods-obtaining-images.md), [4-4 鏡像的獲取和查看](./4-4-image-basic.md)
- `docker image ls`  
  - 功能：列出本地已有的 Docker 鏡像。
  - 出現章節：[4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-5 docker鏡像的導入和導出](./4-5-load-and-save-image.md), [4-7 鏡像的構建和分享](./4-7-build-and-share-images.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md)
- `docker image inspect <image_id>`  
  - 功能：顯示特定 Docker 鏡像的詳細信息。
  - 說明：
    - `<image_id>` 是鏡像的 ID，可以通過 `docker image ls` 命令查看。
    - 顯示的資訊包含：ID、架構、大小、分層信息、作業系統 (OS) 等。
  - 出現章節：[4-4 鏡像的獲取和查看](./4-4-image-basic.md)
- `docker image rm <image_id>`  
  - 功能：刪除 Docker 鏡像。
  - 說明：
    - `<image_id>` 是鏡像的 ID，可以通過 `docker image ls` 命令查看。
    - 如果鏡像正在被使用，則需要先停止並刪除使用該鏡像的容器才能刪除鏡像。
    - 如果要刪除的鏡像 ID 前幾碼相同，則無法刪除，必須使用完整的 ID。
  - 出現章節： [4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-5 docker鏡像的導入和導出](./4-5-load-and-save-image.md)
- `docker image save -o <file_name> <image_name>:<tag>`  
  - 功能：將 Docker 鏡像保存為文件。
  - 說明：
    - `<file_name>` 是保存後的文件名。
    - `<image_name>` 是鏡像的名稱。
    - `<tag>` 是可選的，用於指定鏡像版本，默認為 `latest`。
  - 出現章節：[4-2 鏡像的獲取方式](./4-2-methods-obtaining-images.md), [4-5 docker鏡像的導入和導出](./4-5-load-and-save-image.md)
- `docker image load -i <file_name>`  
  - 功能：從文件導入 Docker 鏡像。
  - 說明：
    - `<file_name>` 是要導入的鏡像文件。
  - 出現章節：[4-2 鏡像的獲取方式](./4-2-methods-obtaining-images.md), [4-5 docker鏡像的導入和導出](./4-5-load-and-save-image.md)
- `docker image history <image_name>`  
  - 功能：查看鏡像的分層歷史記錄，包括每一層的指令和大小。
  - 出現章節：[4-9 聊聊scratch這個鏡像](./4-9-scratch-image.md)
- `docker image tag <source_image_name>:<source_tag> <target_image_name>:<target_tag>`  
  - 功能：為鏡像建立新的標籤。
  - 說明：
    - `<source_image_name>`  是原始鏡像的名稱。
    - `<source_tag>` 是原始鏡像的標籤。
    - `<target_image_name>` 是新鏡像的名稱。
    - `<target_tag>` 是新鏡像的標籤。
    - 通常用於將鏡像推送到 Docker Hub 時指定帶有用戶 ID 的完整鏡像名稱。
  - 出現章節：[4-7 鏡像的構建和分享](./4-7-build-and-share-images.md)

### 鏡像構建 [[↑](#本章-docker-命令---cheat-sheet)]

- `docker image build -t <image_name>:<tag> .`  
  - 功能：使用 Dockerfile 構建鏡像。
  - 說明：
    - `<image_name>` 是鏡像的名稱。
    - `<tag>` 是可選的，用於指定鏡像版本，默認為 `latest`。
    - `.` 代表 Dockerfile 所在的當前目錄。
  - 出現章節：[4-7 鏡像的構建和分享](./4-7-build-and-share-images.md)
- `docker container commit <container_id> <image_name>:<tag>`  
  - 功能：從 Docker 容器創建一個新的鏡像。
  - 說明：
    - `<container_id>` 是容器的 ID，可以通過 `docker container ls -a` 命令查看。
    - `<image_name>` 是新鏡像的名稱。
    - `<tag>` 是可選的，用於指定鏡像版本，默認為 `latest`。
  - 出現章節：[4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md)

### 容器管理 [[↑](#本章-docker-命令---cheat-sheet)]

- `docker container run <options> <image_name>:<tag> <command>`  
  - 功能：創建並啟動一個 Docker 容器。
  - 說明：
    - `<options>` 是可選的，常用的選項包括：
      - `-d`：後臺運行。
      - `-it`：交互式模式。
      - `-p`：端口映射 等。
    - `<image_name>` 是鏡像的名稱。
    - `<tag>` 是可選的，用於指定鏡像版本，默認為 `latest`。
    - `<command>` 是可選的，要在容器中執行的命令。
  - 出現章節：4-4 鏡像的獲取和查看, [4-7 鏡像的構建和分享](./4-7-build-and-share-images.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md), [4-9 聊聊scratch這個鏡像](./4-9-scratch-image.md)
- `docker container ls`  
  - 功能：列出正在運行的 Docker 容器。
  - 出現章節：[4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md)
- `docker container ls -a`  
  - 功能：列出所有 Docker 容器，包括已停止的容器。
  - 出現章節：[4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md)
- `docker container exec -it <container_id> <command>`  
  - 功能：在正在運行的容器中執行命令。
  - 說明：
    - `<container_id>` 是容器的 ID，可以通過 `docker container ls` 命令查看。
    - `<command>` 是要在容器中執行的命令。
    - `-it`  參數允許交互式訪問容器。
  - 出現章節：[4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md)
- `docker container stop <container_id>`  
  - 功能：停止正在運行的 Docker 容器。
  - 說明：
    - `<container_id>` 是容器的 ID，可以通過 `docker container ls` 命令查看。
  - 出現章節：[4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md)
- `docker container rm <container_id>`  
  - 功能：刪除 Docker 容器。
  - 說明：
    - `<container_id>` 是容器的 ID，可以通過 `docker container ls -a` 命令查看。
  - 出現章節：[4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md)

### Docker Hub [[↑](#本章-docker-命令---cheat-sheet)]

- `docker login`
  - 功能：登錄到 Docker Hub。
  - 出現章節：[4-7 鏡像的構建和分享](./4-7-build-and-share-images.md)
- `docker image push <image_name>:<tag>`  
  - 功能：將鏡像推送到 Docker Hub。
  - 說明：
    - `<image_name>` 是鏡像的名稱。Image 的命名方式必須為 `dockerhub_account_id/image_name`
    - `<tag>` 是鏡像的標籤。
    - 您必須先登入 Docker Hub 才能推送。
  - 出現章節：[4-7 鏡像的構建和分享](./4-7-build-and-share-images.md)

### 其他重要概念 [[↑](#本章-docker-命令---cheat-sheet)]

- **Registry**：存放 Docker 鏡像的倉庫，例如 Docker Hub、 Quay.io 等。
- **Dockerfile**：用來構建 Docker 鏡像的文本文件，包含一系列指令。  
- **Base Image**：用作基礎的鏡像，例如 Ubuntu、 CentOS 等操作系統鏡像。
- **Image Layer**：鏡像的分層結構，每一層都是一個文件系統變更。
- **Scratch Image**：一個空的鏡像，可以用作基礎鏡像來構建極簡的鏡像。  

### Cheat sheet [[↑](#本章-docker-命令---cheat-sheet)]

| 類別 | 命令 | 說明 | 出現的章節 |
|---|---|---|---|
| **鏡像管理** | `docker image pull <image_name>:<tag>` | 從 registry 拉取 Docker 鏡像。如果不指定 tag，則默認為 latest。 | [4-2 鏡像的獲取方式](./4-2-methods-obtaining-images.md), [4-4 鏡像的獲取和查看](./4-4-image-basic.md) |
|  | `docker image ls` | 列出本地已有的 Docker 鏡像。 | [4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-5 docker鏡像的導入和導出](./4-5-load-and-save-image.md), [4-7 鏡像的構建和分享](./4-7-build-and-share-images.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md) |
|  | `docker image inspect <image_id>` | 顯示特定 Docker 鏡像的詳細信息，例如 ID、架構、大小、分層信息等。 | [4-4 鏡像的獲取和查看](./4-4-image-basic.md) |
|  | `docker image rm <image_id>` | 刪除 Docker 鏡像。如果鏡像正在被使用，則需要先停止並刪除使用該鏡像的容器才能刪除鏡像。 | [4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-5 docker鏡像的導入和導出](./4-5-load-and-save-image.md) |
|  | `docker image save -o <file_name> <image_name>` | 將 Docker 鏡像保存為文件。 | [4-2 鏡像的獲取方式](./4-2-methods-obtaining-images.md), [4-5 docker鏡像的導入和導出](./4-5-load-and-save-image.md) |
|  | `docker image load -i <file_name>` | 從文件導入 Docker 鏡像。 | [4-2 鏡像的獲取方式](./4-2-methods-obtaining-images.md), [4-5 docker鏡像的導入和導出](./4-5-load-and-save-image.md) |
|  | `docker image history <image_name>` | 查看鏡像的分層歷史記錄，包括每一層的指令和大小。 | [4-9 聊聊scratch這個鏡像](./4-9-scratch-image.md) |
| **鏡像構建** | `docker image build -t <image_name>:<tag> <Dockerfile 所在路徑>` |  使用 Dockerfile 構建鏡像。 `-t`  參數指定鏡像名稱和標籤。 | [4-7 鏡像的構建和分享](./4-7-build-and-share-images.md) |
|  | `docker container commit <container_id> <image_name>:<tag>` |  從 Docker 容器創建一個新的鏡像。 | [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md) |
| **容器管理** | `docker container run <options> <image_name> <command>` |  創建並啟動一個 Docker 容器。常用的選項包括： `-d` (後臺運行)、 `-it` (交互式模式)、 `-p` (端口映射) 等。 | [4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-7 鏡像的構建和分享](./4-7-build-and-share-images.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md), [4-9 聊聊scratch這個鏡像](./4-9-scratch-image.md) |
|  | `docker container ls` |  列出正在運行的 Docker 容器。 | [4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md) |
|  | `docker container ls -a` | 列出所有 Docker 容器，包括已停止的容器。 | [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md) |
|  | `docker container exec -it <container_id> <command>`  | 在正在運行的容器中執行命令。 `-it` 參數允許交互式訪問容器。 | [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md) |
|  | `docker container stop <container_id>` | 停止正在運行的 Docker 容器。 | [4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md) |
|  | `docker container rm <container_id>` | 刪除 Docker 容器。 | [4-4 鏡像的獲取和查看](./4-4-image-basic.md), [4-8 通過commit創建鏡像](./4-8-build-image-via-commit.md) |
| **Docker Hub** | `docker login` | 登錄到 Docker Hub。 | [4-7 鏡像的構建和分享](./4-7-build-and-share-images.md) |
|  | `docker image push <image_name>:<tag>` | 將鏡像推送到 Docker Hub。 | [4-7 鏡像的構建和分享](./4-7-build-and-share-images.md) |
|  | `docker image tag <image_name>:<tag> <new_image_name>:<new_tag>` | 為鏡像創建一個新的標籤，通常用於將鏡像推送到 Docker Hub 時指定帶有用戶 ID 的完整鏡像名稱。 | [4-7 鏡像的構建和分享](./4-7-build-and-share-images.md) |
