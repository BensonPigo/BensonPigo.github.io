
# Go 版本

1. 專案目錄建立，例如目錄名稱為：ScriptPilot
2. 初始化 Go 模組：
```
go mod init ScriptPilot
```

3. 設置 Protobuf 文件
   1. 創建 proto 資料夾，並新增 taskexecutor.proto 文件。
   2. 內容範例：
```
syntax = "proto3";

package taskexecutor;

option go_package = "ScriptPilot/proto/taskexecutor";

service TaskExecutor {
  rpc ExecuteTask (TaskRequest) returns (TaskResponse);
}

message TaskRequest {
  string task_name = 1; // 任務名稱
}

message TaskResponse {
  string message = 1;   // 執行結果訊息
  string output = 2;    // 腳本執行輸出
  string error = 3;     // 錯誤訊息（如有）
}

```
4. 編譯 Protobuf
- 專案的根目錄，安裝 protoc 和 Go 插件
```
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
```
-安裝完成後，使用版本指令檢查是否安裝成功
```
protoc --version
```
- 專案的根目錄，執行編譯命令，生成 Go 文件 (*.pb.go)
```
protoc --go_out=. --go-grpc_out=. proto/taskexecutor.proto
```
- 重要編譯命令說明
> 當前目錄：這邊要注意，參數中用到 . 代表當前目錄，當前目錄指的是「.proto 文件中的 option go_package」，不是 「ScriptPilot根目錄」

> go_out：表示生成的 Go 文件(*.pb.go)會放在哪一個目錄下

> go-grpc_out：表示生成的 gRPC 文件(*_grpc.pb.go)會放在哪一個目錄下

> proto/taskexecutor.proto：要執行編譯的 Protobuf 文件

- 其他可選參數
> proto_path：用於指定 .proto 文件的搜索路徑。如果你的 .proto 文件不在當前目錄，可以額外指定

> plugin：用於指定自定義插件。如果你安裝的 protoc-gen-go 和 protoc-gen-go-grpc 插件沒有在 PATH 中，可以通過該參數指定具體的插件路徑

5. 檢查指令生成的Go 文件，會位於 proto/ 資料夾
- taskexecutor.pb.go
- taskexecutor_grpc.pb.go






   
