# 前言
自學Golang一陣子，開始嘗試side project之後，發現對於專案目錄的布局是一門學問。由於先前的經驗都是C#以及.NET相關的開發框架，Golang的語言特性，讓習慣.NET那一套方式的我頓時摸不著頭緒，因此決定寫下研究過程。

# 疑惑
研究過程，我想能見度最高的應該非 [Standard Go Project Layout](https://github.com/golang-standards/project-layout) 莫屬了，但細看會發現其實算是個大雜燴，在不同框架、資料庫、有無整合前端的情境下，目錄佈局會有各自的特色。

# 學習過程與發現
決定另尋出路後，找到兩大方向，從快速理解各種情境的佈局，提供範本；到深入理解package特性，程式碼邊界，將這兩大方向的特行整合，算是找出了一條不錯到道路。

## 超級工具 - [Go-Blueprint](https://github.com/Melkeydev/go-blueprint)

Go Blueprint提供了佈局範例，甚至是專案建立指令，完全是超級懶人包 [Go-Blueprint Dev](https://go-blueprint.dev/)。無論是基礎的hello word，還是整合眾多功能的專案，在[Go-Blueprint Docs](https://docs.go-blueprint.dev/)都可以找到快速加設起專案佈局與所需資源的指令參數。

## Udemy課程
在課程內容中，講師也說明了一套根據自身經驗，所總結出的佈局邏輯。


## 最佳實踐，以blog 系統為例

1. config/：應用程式初始化設定，系統參數，密鑰...等等
2. database/：與資料庫相關的基礎功能(如連線)，資料模型相關method
3. 待續...

```
your-project/
├── config/
│   └── log.yaml
│   └── key.yaml
│   └── mysql.yaml
│   └── redis.yaml
├── database/
│   │   └── test/
│   └── blog.go
│   └── db_connection.go
│   └── dual_token.go
│   └── user.go
├── cmd/
│   ├── app1/
│   │   └── main.go
│   └── app2/
│       └── main.go
├── internal/
│   ├── somepkg/
│   │   └── somefile.go
│   └── otherpkg/
│       └── otherfile.go
├── pkg/
│   ├── publicpkg1/
│   │   └── publicfile.go
│   └── publicpkg2/
│       └── anotherfile.go
├── api/
│   ├── v1/
│   │   └── api.proto
│   └── v2/
│       └── api.proto
├── scripts/
│   └── build.sh
├── docs/
│   └── design.md
├── test/
│   └── some_external_tests.go
├── go.mod
└── README.md
```
