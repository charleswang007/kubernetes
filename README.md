# Kubernetes
## Docker vs. VM
Docker的輕量虛擬化的技術及易於移植的特性，非常利於現代雲端服務的開發及部署。相對來說，傳統的虛擬機需要追求高規格，且在基礎設施和維運(Ops)上需要花費非常多的工夫和心力。以下是傳統虛擬機器與Docker容器所做的比較[1]：
Docker容器	傳統VM
虛擬化技術	以應用程式為中心	以作業系統為中心
安裝作業系統	不需要，故啟動快	需要，故啟動慢
標準化	利用Docker映像檔便可輕易複製開發環境	各家標準不同，作業系統核心也不一樣，移植困難
對DevOps的作用	Dockerfile將參數、環境完整的紀錄下來並結合版本控制CI/CD工具	整合DevOps工具相對困難


## Monolithic-service vs. Microservice
微服務(microservices)架構將每一個具有商業邏輯的服務獨立出來，例如不再將所有資料都寫入同一個資料庫，而是每個單獨的服務都有一個最適合自己本身結構的資料庫。好處是讓每個服務都可以用最適合自己的語言、資料庫來開發。從下圖可以看到，乘客管理、Web UI、金流等都是一個獨立出來的微服務，而每個服務都開放了REST API實行客戶端或者服務之間的溝通。在實作上，每一個商業功能/服務都可能是一台VM或者一個容器。
![alt text](microservice.png "microservice")

## K8S and microservice
Kubernetes特別適合微服務這樣的架構。將數個容器組合起來成一個服務(Service，註：Service是K8S的專有名詞，下面會介紹)，Kubernetes也提供了良好的服務發現(Service discovery)機制，讓每個服務彼此可以通信。最重要的是K8S強大的編程可以自動擴展服務，甚至還可以對大規模的容器作滾動更新(Rolling update)以及回滾機制(Rolling back/Undo)，更可以整合CI/CD等DevOps的工具，絕對讓您用最小的力氣管理最龐大的系統。

## Kubernetes architecture
Using kubernetes with [Google Container Engine (GKE)](https://cloud.google.com/container-engine/docs/).
K8S屬分布式系統，主要元件有：
Master – 大總管，可做為主節點
Node – 主要工作的節點，上面運行了許多容器。可想作一台虛擬機。K8S可操控高達1,000個nodes以上
masters和nodes組成叢集(Clusters)
![alt text](k8s_arch.png "K8S Architecture")
Master 包含了三個基本組件 Etcd, API Server, Controller Manager Server。

Server Node 包含了四個基本組件 Kubelet, Proxy, Pod, Container。





