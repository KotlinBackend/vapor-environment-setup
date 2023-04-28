# Vapr 在 Ubuntu22.04 上的開發環境建置

## 1 Vapr 是什麼

Vapor[^1] 是一個用 Swift 程式語言開發的 Web Framework，可運行在 macOS 跟 Linux 上。

如果想在 linux 上開發 Vapor Web 應用程式，需要先安裝 Swift 程式開發工具

然後再安裝 Vapor[^1] 的開發工具

## 2 概念圖

![](https://i.imgur.com/tEPKyYN.png)

## 3 安裝步驟

本文將會以 Ubuntu22.04 OS

使用 vscode 作為開發整合環境

逐步講解安裝步驟

### 3.1 安裝 Swift[^3]

到 [Swift 官網](https://www.swift.org/download/)[^3] 下載想要安裝的版本

這裡以 swift-5.8-RELEASE-ubuntu22.04.tar.gz 作為範例

使用以下指令解壓縮該檔案

```shell
tar xzf swift-5.8-RELEASE-ubuntu22.04.tar.gz 
```

把可解壓縮完的執行檔案放置到選定好的執行目錄

```shell
sudo mv swift-5.8-RELEASE-ubuntu22.04 /usr/share/swift
```

設定配置環境變數到 ~/.bashrc

在最後一行加入以下設定

```yaml
export PATH="/usr/share/swift/usr/bin:$PATH"
```

重新讀入環境參數

```shell
source ~/.bashrc
```

查看 swift 安裝結果

使用以下指令

```shell
swift --version
```

如果安裝正確應該會有以下回應
```shell
Swift version 5.8 (swift-5.8-RELEASE)
Target: x86_64-unknown-linux-gnu
```
### 3.2 安裝 Vapor [^1]

首先下載 Vapor 安裝工具

透過 git clone 的方式

```shell
git clone https://github.com/vapor/toolbox.git
```

切換到該目錄

```shell
cd toolbox
```

可以到 [releases](https://github.com/vapor/toolbox/releases)[^4] 查看版本

以下使用 18.6.0

所以 checkout 到該版本
```shell
git checkout 18.6.0
```

編譯為執行檔
```shell
swift build -c release --disable-sandbox
```

把編譯出來的執行檔移動到 /usr/local/bin：

```shell
sudo mv .build/release/vapor /usr/local/bin
```

驗證 vapor 安裝結果
```shell
vapor --help
```
![](https://i.imgur.com/7nMmvIy.png)

## 建制一個新專案

首先建制一個 vapor 專案

```shell
vapor new hello_world
```

用 vscode 開啟該專案

執行 
```shell
swift run
```
![](https://i.imgur.com/bvFep7f.png)


查看 http://localhost:8080/hello

![](https://i.imgur.com/9logYI4.png)

## References

[^1]: [Vapor](https://vapor.codes/)

[^2]: [使用WSL開發vapor](https://riddleling.site/?p=1726) 

[^3]: [swift官方網站](https://www.swift.org/download/)

[^4]: [releases](https://github.com/vapor/toolbox/releases)