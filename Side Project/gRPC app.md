# gRPC Side Project

## 背景說明

公司有許多工廠的 Region，共 10 區，且全部純地端。

## 困境

工廠 Server 上存放許多.Net Framewrok 應用程式，以 Win Task 定時執行。若全廠區需手動執行，台北的人員需要遠端到 10 台 Server，手動執行，並且不斷連回去檢查完成了沒，十分麻煩。

## 思路

1. 台北架設一個簡單的 Web Application，用於發送指令，指令內容為：Region、欲執行的 DLL 路徑、Method、參數
2. Command 服務，放在工廠，作為 gRPC Client，用於接收台北的指令，根據 DLL 路徑、Method、參數，執行 gRPC Server 對應的 method，並且記錄所有接收、執行過的指令。
3. DLL 讀取服務，放在工廠，作為 gRPC Server，去 Invoke 所有 Win Task 應用程式的 dll，提供給 Command 服務呼叫

## 流程圖
