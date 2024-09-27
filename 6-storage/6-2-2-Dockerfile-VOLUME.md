<!-- This md file is originally converted from onenote -->

# [6-2-2 Dockerfile `VOLUME` 補充](https://dockertips.readthedocs.io/en/latest/docker-volume/data-volume.html#v)

2023年2月25日
下午 04:56

## Contents [[↑](#6-2-2-dockerfile-volume-補充)]

- [6-2-2 Dockerfile `VOLUME` 補充](#6-2-2-dockerfile-volume-補充)
  - [Contents \[↑\]](#contents-)
    - [Dockerfile 中定義 `VOLUME` 路徑的作用 \[↑\]](#dockerfile-中定義-volume-路徑的作用-)
    - [總結 \[↑\]](#總結-)

### Dockerfile 中定義 `VOLUME` 路徑的作用 [[↑](#6-2-2-dockerfile-volume-補充)]

- 當創建容器時, 若**沒有使用 `-v` 參數**, 因為 Dockerfile 中有定義 `VOLUME`, 則 docker 會自動產生一個以隨機 hash 命名的匿名 volume 與 Dockerfile 中定義 `VOLUME` 路徑綁定.

- 當創建容器時, 且**使用 `-v` 參數**, 這個 `-v` 可以將一個 volume 或 bind mount 路徑與容器內的任何路徑綁定, 這個容器內的任何路不一定要與 Dockerfile 中的 `VOLUME` 路徑相同. 即使 Dockerfile 中沒有定義 `VOLUME`, 依然可以使用 `-v` 參數
  - 當使用 `-v` 參數將一個 volume 或 bind mount 路徑與 Dockerfile 中的 `VOLUME` 路徑綁定時, docker 則不再創建匿名 volume
  - 當使用 `-v` 參數將一個 volume 或 bind mount 路徑與一個**非** Dockerfile 中的 `VOLUME` 路徑綁定時, docker 仍然會為 Dockerfile 中定義的 `VOLUME` 路徑創建匿名卷. 此時, 這個容器會同時使用兩個卷:
    - `-v` 參數中指定的 volume 或 bind mount 路徑
    - 一個匿名卷

### 總結 [[↑](#6-2-2-dockerfile-volume-補充)]

- Dockerfile 中定義的 `VOLUME` 指令在沒有使用 `-v` 參數掛載到同一路徑時會自動創建匿名 volume.
- Dockerfile 中定義的 `VOLUME` 指令在使用 `-v` 參數掛載到同一路徑時會被覆蓋. 此時, Docker 不會再創建匿名卷.
- `-v` 只會覆蓋與其掛載路徑相同的 `VOLUME` 定義，不會影響到其他路徑的 `VOLUME` 指令以及匿名 volume 的創建.
