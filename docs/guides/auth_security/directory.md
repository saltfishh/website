---
sidebar_position: 6
---

# 服务目录

介绍Keystone维护的服务目录的工作原理。 Keystone服务目录定义了区域，服务，以及服务在指定区域内的接入端点。

## 区域（region)

区域定义了一个部署区域。当给用户部署了多套服务，为了区分，则给每套服务分配一个区域标识。当访问服务时，通过指定区域，可以获得同一服务在不同区域的接入端点，从而允许多套相同服务的共存。

### 限制

当该区域下有接入端点时，无法删除该区域


## 服务(service)

服务定一个了一个提供API的服务

### 服务属性

字段    | 说明
--------|---------------------
id      | 服务ID，不可变ID	
name    | 服务名称	
type    | 服务类型，典型的服务类型有：compute, image, identity, k8s, meter等
enabled	| 服务是否启用	

### 限制

当有该服务的接入端点定义时，无法删除该服务

服务启用时无法删除


## 服务接入点(endpoints)

接入点定义了一个服务在指定区域的服务URL。分为public/internal和admin等类型。

### 接入端点属性

| 字段        | 说明                                                                                                                                                                                            |
| ----------- | -----------------                                                                                                                                                                               |
| id          | ID                                                                                                                                                                                              |
| name        | 名称                                                                                                                                                                                            |
| region_id   | 服务接入点的归属区域                                                                                                                                                                            |
| service_id  | 服务接入点的归属服务                                                                                                                                                                            |
| url         | 接入端点的访问URL                                                                                                                                                                               |
| interface   | 接入端点的接口类型，目前支持internal/public/admin/console四个类型，默认使用internal类型的接入端点。当定义了一个服务的console类型的接入端点，则会在前端控制台的服务目录里显示跳转到该URL的链接 |
| enabled     | 接入端点是否启用                                                                                                                                                                                |

### 限制

当该接入端点启用时，不能删除