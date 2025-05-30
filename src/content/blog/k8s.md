# Kubernetes 入门学习笔记

> 基于郑光力的 [Kubernetes 入门教程](https://guangzhengli.com/courses/kubernetes/pre) 整理  
> 最后更新: 2023年10月

## 目录
- [一、Kubernetes 核心概念](#一kubernetes-核心概念)
- [二、集群架构详解](#二集群架构详解)
- [三、核心对象解析](#三核心对象解析)
- [四、实践操作指南](#四实践操作指南)
- [五、学习总结与计划](#五学习总结与计划)

---

## 一、Kubernetes 核心概念

### 1.1 什么是 Kubernetes？
- **容器编排系统**：自动化部署、扩展和管理容器化应用
- **核心价值**：
    - ⚙️ 自动化运维：自我修复、滚动更新、自动扩缩容
    - 🔗 服务编排：服务发现、负载均衡、存储编排
    - 📦 环境一致性：开发-测试-生产环境统一
- **发展历程**：
    - Google Borg 系统的开源版本
    - 2014年正式发布，现由 CNCF 托管

### 1.2 基本术语
| 术语 | 说明 | 类比 |
|------|------|------|
| **Pod** | 最小部署单元，包含1个或多个容器 | 虚拟机 |
| **Node** | 工作节点，运行Pod的机器 | 物理服务器 |
| **Cluster** | 由Master和Node组成的集群 | 数据中心 |
| **Deployment** | 声明式更新Pod的控制器 | 部署脚本 |
| **Service** | 定义Pod访问策略的抽象层 | 负载均衡器 |

---

## 二、集群架构详解

### 2.1 Master 节点组件
```mermaid
graph LR
    A[API Server] --> B[etcd]
    A --> C[Scheduler]
    A --> D[Controller Manager]