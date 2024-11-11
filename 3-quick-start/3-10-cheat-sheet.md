# 本章 Docker 命令 - Cheat Sheet

## Contents [[↑](#本章-docker-命令---cheat-sheet)]

- [本章 Docker 命令 - Cheat Sheet](#本章-docker-命令---cheat-sheet)
  - [Contents \[↑\]](#contents-)
    - [資訊查詢 \[↑\]](#資訊查詢-)
    - [命令用法 \[↑\]](#命令用法-)
    - [容器管理 \[↑\]](#容器管理-)
    - [映像管理 \[↑\]](#映像管理-)
    - [容器操作 \[↑\]](#容器操作-)
    - [Cheat sheet \[↑\]](#cheat-sheet-)

以下是本章所使用的 Docker 命令，並根據其功能分類，同時指出了命令出現的章節:

### 資訊查詢 [[↑](#本章-docker-命令---cheat-sheet)]

- `docker version`
  - 功能：顯示本地安裝的 Docker 版本，包含 client 和 server 版本資訊。
  - 出現章節：[3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-version-)

- `docker info`
  - 功能：顯示當前 Docker 環境的基本狀態，包含 client、server、container、image、volume 和 network 等資訊。
  - 出現章節：[3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-info-)

### 命令用法 [[↑](#本章-docker-命令---cheat-sheet)]

- `docker`
  - 功能：顯示 Docker 命令的用法和結構，包含可用的 options、management commands 和 commands。
  - 出現章節：[3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-)

### 容器管理 [[↑](#本章-docker-命令---cheat-sheet)]

- `docker container ls`
  - 功能：列出當前正在執行的容器。
  - 出現章節：[3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-container-), [3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md), [3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md)

- `docker container ls -a`
  - 功能：列出當前所有容器，包括已停止的容器。
  - 出現章節：[3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-container-), [3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md)

### 映像管理 [[↑](#本章-docker-命令---cheat-sheet)]

- `docker image ls`
  - 功能：列出當前系統上的所有映像。
  - 出現章節：[3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-image-)

- `docker image rm <image_name>`
  - 功能：刪除指定的 Docker 鏡像。
  - 說明：
    - `<image_name>` 是要刪除的鏡像的名稱。
  - 出現章節：[3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-image-)

### 容器操作 [[↑](#本章-docker-命令---cheat-sheet)]

- `docker container run <image_name>`
  - 功能：創建並運行一個 Docker 容器。
  - 說明：
    - `<image_name>` 是要使用的 Docker 鏡像的名稱。
  - 出現章節：[3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md), [3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md), [3-9 容器和虛擬機](./3-9-behind-the-scenes-when-creating-container.md)

- `docker container stop <container_id>/<container_name>`
  - 功能：停止指定的 Docker 容器。
  - 說明：
    - `<container_id>` 或 `<container_name>` 是要停止的容器的 ID 或名稱。
  - 出現章節：[3-5 命令行小技巧之批量操作](./3-5-bulk-commands-for-containers.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md)

- `docker container ls -a`
  - 功能：列出所有容器，包括正在運行的和已退出的容器。
  - 出現章節：[3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md)

- `docker container rm <container_id>/<container_name>`
  - 功能：刪除指定的 Docker 容器。
  - 說明：
    - `<container_id>` 或 `<container_name>` 是要刪除的容器的 ID 或名稱。
  - 出現章節：[3-4 創建第一個容器](./3-4-first-container.md), [3-5 命令行小技巧之批量操作](./3-5-bulk-commands-for-containers.md)

- `docker container rm -f <container_id>/<container_name>`
  - 功能：強制刪除指定的 Docker 容器，即使容器正在運行。
  - 說明：
    - `<container_id>` 或 `<container_name>` 是要刪除的容器的 ID 或名稱。
  - 出現章節：[3-5 命令行小技巧之批量操作](./3-5-bulk-commands-for-containers.md)

- `docker container logs <container_id>/<container_name>`
  - 功能：查看指定容器的日誌。
  - 說明：
    - `<container_id>` 或 `<container_name>` 是要查看日誌的容器的 ID 或名稱。
  - 出現章節：[3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md)

- `docker container logs -f <container_id>/<container_name>`
  - 功能：動態跟蹤指定容器的日誌。
  - 說明：
    - `<container_id>` 或 `<container_name>` 是要跟蹤日誌的容器的 ID 或名稱。
  - 出現章節：[3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md)

- `docker container exec -it <container_id>/<container_name> <command>`
  - 功能：以交互模式在正在運行的容器中執行命令。
  - 說明：
    - `<container_id>` 或 `<container_name>` 是要進入的容器的 ID 或名稱
    - `<command>` 是要在容器中執行的命令。
  - 出現章節：[3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md), [3-9 容器和虛擬機](./3-9-behind-the-scenes-when-creating-container.md)

- `docker container top <container_id>/<container_name>`
  - 功能：顯示指定容器中運行的進程信息。
  - 說明：
    - `<container_id>` 或 `<container_name>` 是要查看進程信息的容器的 ID 或名稱。
  - 出現章節：[3-9 容器和虛擬機](./3-9-behind-the-scenes-when-creating-container.md)

### Cheat sheet [[↑](#本章-docker-命令---cheat-sheet)]

| 類別 | 命令 | 說明 | 出現的章節 |
|---|---|---|---|
| 資訊查詢 | `docker version` | 顯示本地安裝的 Docker 版本 | [3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-version-) |
|  | `docker info` | 顯示當前 Docker 環境的基本狀態 | [3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-info-) |
| 命令用法 | `docker` | 顯示 Docker 命令的用法和結構 | [3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-) |
| 容器管理 | `docker container ls` | 列出當前正在執行的容器 | [3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-container-), [3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md), [3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md) |
|  | `docker container ls -a` | 列出當前所有容器，包括已停止的容器 | [3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-container-), [3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md) |
| 映像管理 | `docker image ls` | 列出當前系統上的所有映像 | [3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-image-) |
|  | `docker image rm <image_name>` | 刪除指定的 Docker 鏡像 | [3-2 認識 Docker 的命令行](./3-2-docker-basic-commands.md#docker-image-) |
| 容器操作 | `docker container run <image_name>` | 創建並運行一個 Docker 容器 | [3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md), [3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md), [3-9 容器和虛擬機](./3-9-behind-the-scenes-when-creating-container.md) |
|  | `docker container stop <container_id>/<container_name>` | 停止指定的 Docker 容器 | [3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md) |
|  | `docker container ls -a` | 列出所有容器，包括正在運行的和已退出的容器 | [3-4 創建第一個容器](./3-4-first-container.md), [3-6 容器的 attached 和 detached 模式](./3-6-attached-and-detached-modes.md) |
|  | `docker container rm <container_id>/<container_name>` | 刪除指定的 Docker 容器 | [3-4 創建第一個容器](./3-4-first-container.md), [3-5 命令行小技巧之批量操作](./3-5-bulk-commands-for-containers.md) |
|  | `docker container rm -f <container_id>/<container_name>` | 強制刪除指定的 Docker 容器 | [3-5 命令行小技巧之批量操作](./3-5-bulk-commands-for-containers.md) |
|  | `docker container logs <container_id>/<container_name>` | 查看指定容器的日誌 | [3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md) |
|  | `docker container logs -f <container_id>/<container_name>` | 動態跟蹤指定容器的日誌 | [3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md) |
|  | `docker container exec -it <container_id>/<container_name> <command>` | 以交互模式在正在運行的容器中執行命令 | [3-7 容器的交互模式](./3-7-how-Windows-and-Mac-run-docker-engine.md), [3-9 容器和虛擬機](./3-9-behind-the-scenes-when-creating-container.md) |
|  | `docker container top <container_id>/<container_name>` | 顯示指定容器中運行的進程信息 | [3-9 容器和虛擬機](./3-9-behind-the-scenes-when-creating-container.md) |
