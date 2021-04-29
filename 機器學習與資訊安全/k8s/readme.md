#
```
Kubernetes 30天學習筆記系列 
https://ithelp.ithome.com.tw/articles/10192401
```

# 
```
第8章 搭建Kubernetes集群
8.1 Docker+Kubernetes已成為雲計算的主流
8.1.1 什麼是Kubernetes
8.1.2 Kubernetes正在塑造應用程式開發和管理的未來

8.2 Kubernetes主體架構
8.2.1 主要核心組件
8.2.2 基本概念

8.3 使用Minikube部署本地Kubernetes集群
8.3.1 什麼是Kubernetes集群
8.3.2 使用Minikube創建本地Kubernetes實驗環境

8.4 使用kubectl管理Kubernetes集群
8.4.1 概述
8.4.2 語法
8.4.3 主要命令說明
8.4.4 資源類型說明
8.4.5 命令標誌說明
8.4.6 格式化輸出

8.5 使用kubeadm創建集群
8.5.1 kubeadm概述
8.5.2 kubelet概述
8.5.3 定義集群部署目標和規劃
8.5.4 開始部署
8.5.5 主節點部署
8.5.6 工作節點部署
8.5.7 安裝儀錶盤

8.6 集群故障處理
8.6.1 健康狀態檢查——初診
8.6.2 進一步診斷分析——聽診三板斧
8.6.3 容器調測
8.6.4 對症下藥
8.6.5 部分常見問題處理
8.6.6 小結


第9章 將應用部署到Kubernetes集群
9.1 使用kubectl部署應用
9.1.1 kubectl部署流程
9.1.2 部署一個簡單的Demo網站
9.2 應用伸縮和回滾
9.2.1 使用“kubectl scale”命令來伸縮應用
9.2.2 使用“kubectl autoscale”命令來自動伸縮應用
9.2.3 使用“kubectl run”命令快速運行應用
9.2.4 使用“kubectl set”命令更新應用
9.2.5 使用“kubectl rollout”命令回滾應用

9.3 通過Service訪問應用
9.3.1 通過Pod IP訪問應用
9.3.2 通過ClusterIP Service在集群內部訪問
9.3.3 通過NodePort Service在外部訪問集群應用
9.3.4 通過LoadBalancer Service在外部訪問集群應用
9.3.5 Microsoft SQL Server資料庫實戰

9.4 使用Ingress負載分發微服務
9.4.1 Demo規劃
9.4.2 準備Demo並完成部署
9.4.3 創建部署資源
9.4.4 創建服務資源
9.4.5 創建Ingress資源並配置轉發規則

9.5 利用Helm簡化Kubernetes應用部署
9.5.1 Helm基礎
9.5.2 安裝Helm
9.5.3 使用Visual Studio 2019為Helm編寫一個簡單的應用
9.5.4 定義charts
9.5.5 使用Helm部署Demo
9.5.6 Helm常用操作命令


第10章 將應用託管到雲端
10.1 什麼是雲計算
10.1.1 為什麼要上雲
10.1.2 雲計算的三種部署方式
10.1.3 雲服務的類型
10.2 Docker+k8s是上雲的不二選擇
10.2.1 上雲的問題
10.2.2 利用Docker+k8s解決傳統應用上雲問題
10.3 主流雲計算容器服務介紹
10.3.1 亞馬遜AWS
10.3.2 微軟Azure
10.3.3 阿裡雲
10.3.4 騰訊雲
10.4 自建還是託管
10.4.1 自建容器服務存在的問題
10.4.2 雲端容器服務的優勢
10.5 一般應用服務部署流程
10.5.1 創建集群和節點
10.5.2 創建命名空間和鏡像
10.5.3 創建服務
10.5.4 配置鏡像觸發器
10.5.5 推送鏡像
10.6 如何節約雲端成本
10.6.1 無須過度購買配置，儘量使用自動擴展
10.6.2 最大化地利用伺服器資源
10.6.3 使用Ingress節約負載均衡資源
10.6.4 使用NFS盤節約存儲成本
10.7 問題處理
10.7.1 鏡像拉取問題
10.7.2 綁定雲硬碟之後Pod的調度問題
10.7.3 遠端登入
10.7.4 利用日誌來排查問題



第11章 容器化後DevOps之旅
11.1 DevOps基礎知識
11.1.1 什麼是DevOps
11.1.2 為什麼需要DevOps
11.1.3 DevOps對應用程式發佈的影響
11.1.4 如何實施DevOps

11.2 Docker與持續集成和持續部署
11.2.1 Docker與持續集成和持續部署
11.2.2 參考流程


11.3 使用Azure DevOps完成CI/CD
11.3.1 適用於容器的CI/CD流程
11.3.2 使用Azure DevOps配置一個簡單的CI/CD流程

11.4 使用Tencent Hub完成CI/CD
11.4.1 關於Tencent Hub
11.4.2 使用Tencent Hub配置一個簡單的CI流程
11.4.3 直接使用容器服務的鏡像構建功能

11.5 使用內部管理工具完成CI/CD流程
11.5.1 一個簡單的CI/CD流程
11.5.2 關於TeamCity
11.5.3 運行TeamCity Server
11.5.4 運行TeamCity Agent
11.5.5 連接和配置Agent
11.5.6 創建專案以及配置CI
11.5.7 使用Jenkins完成CI/CD
```
