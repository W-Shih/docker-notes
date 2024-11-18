# [8-9 水平擴展和負載均衡](https://dockertips.readthedocs.io/en/latest/docker-compose/compose-scale.html)

2024年11月7日
下午 09:32

## Contents [[↑](#8-9-水平擴展和負載均衡)]

- [8-9 水平擴展和負載均衡](#8-9-水平擴展和負載均衡)
  - [Contents \[↑\]](#contents-)
    - [環境搭建 \[↑\]](#環境搭建-)
    - [水平擴展 \[↑\]](#水平擴展-)
      - [`--scale` 的負載均衡 \[↑\]](#--scale-的負載均衡-)
      - [環境清理 \[↑\]](#環境清理-)
    - [添加 nginx 與水平擴展 \[↑\]](#添加-nginx-與水平擴展-)
      - [效果 \[↑\]](#效果-)

### 環境搭建 [[↑](#8-9-水平擴展和負載均衡)]

- `docker-compose.yml`

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_000.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_001.png" /></p>
        </td>
      </tr>
    </tbody>
  </table>

- 啟動
  - `$ docker-compose pull`
  - `$ docker-compose build`
  - `$ docker-compose up -d`
  - `$ docker-compose ps`

    <table>
      <colgroup>
        <col style="width: 100%" />
      </colgroup>
      <thead>
        <tr class="header">
          <th>
            <p><img src="assets/008_8-9_水平擴展和負載均衡_002.png" /></p>
          </th>
        </tr>
      </thead>
      <tbody>
      </tbody>
    </table>

- 網路通信

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_003.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_004.png" /></p>
        </td>
      </tr>
    </tbody>
  </table>

### 水平擴展 [[↑](#8-9-水平擴展和負載均衡)]

- 向上 scale, `$ docker-compose up -d` **`--scale flask=3`**

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_005.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>

- 向下 scale, `$ docker-compose up -d` **`--scale flask=1`**

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_006.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>

#### `--scale` 的負載均衡 [[↑](#8-9-水平擴展和負載均衡)]

- 準備

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_007.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>

- `ping`

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_008.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>

- `curl`

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_009.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>

#### 環境清理 [[↑](#8-9-水平擴展和負載均衡)]

- `$ docker-compose stop`
- `$ docker-compose rm`

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_010.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
    </tbody>
  </table>

### 添加 nginx 與水平擴展 [[↑](#8-9-水平擴展和負載均衡)]

- [代碼下載](https://dockertips.readthedocs.io/en/latest/docker-compose/compose-scale.html#nginx)

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_011.png" /></p>
          <ul class="incremental">
            <li>
              <p>將 proxy 指向 flask:5000</p>
            </li>
            <li>
              <p>如果有多個 flask 服務實例, docker 會幫我們做負載均衡</p>
            </li>
          </ul>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_012.png" /></p>
          <ul class="incremental">
            <li>
              <p>depends_on 定義服務請動順序</p>
            </li>
            <li>
              <p>bind mount</p>
              <ul class="incremental">
                <li>
                  <p>用 bind mount 將 conf 文件複製進 container</p>
                </li>
                <li>
                  <p>用 bind mount 將 container 的 log 映射到本地</p>
                </li>
              </ul>
            </li>
            <li>
              <p>Network</p>
              <ul class="incremental">
                <li>
                  <p>Backend for flask and redis-sever</p>
                </li>
                <li>
                  <p>Frontend for flask and nginx</p>
                </li>
              </ul>
            </li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>

- `$ docker-compose up -d`

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_013.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_014.png" /></p>
        </td>
      </tr>
      <tr class="even">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_015.png" /></p>
        </td>
      </tr>
      <tr class="odd">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_016.png" /></p>
        </td>
      </tr>
    </tbody>
  </table>

#### 效果 [[↑](#8-9-水平擴展和負載均衡)]

- 單一 container

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_017.png" /></p>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_018.png" /></p>
        </td>
      </tr>
    </tbody>
  </table>

- -`-scale` to 3

  <table>
    <colgroup>
      <col style="width: 100%" />
    </colgroup>
    <thead>
      <tr class="header">
        <th>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_019.png" /></p>
          <ul class="incremental">
            <li>
              <p>需要從新啟動 nginx</p>
            </li>
          </ul>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr class="odd">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_020.png" /></p>
        </td>
      </tr>
      <tr class="even">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_021.png" /></p>
        </td>
      </tr>
      <tr class="odd">
        <td>
          <p><img src="assets/008_8-9_水平擴展和負載均衡_022.png" /></p>
        </td>
      </tr>
    </tbody>
  </table>
