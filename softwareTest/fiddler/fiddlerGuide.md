# Fiddler 使用指南

**Fiddler** 是一款功能强大的网络调试代理工具，用于捕获和分析 HTTP 和 HTTPS 请求。它广泛应用于开发者和测试人员的工作中，用于分析网络流量、调试 API、测试安全性等。

---

## **什么是 Fiddler？**

Fiddler 是由 Telerik 开发的一款跨平台 Web 调试工具。它的主要功能是作为代理服务器拦截客户端和服务器之间的 HTTP/HTTPS 请求和响应。

### **适用场景**
1. 调试 Web 应用程序的请求和响应。
2. 分析网络流量以检测错误或性能问题。
3. 测试 API 请求。
4. 模拟慢速网络。
5. 修改请求或响应内容。
6. 检测安全漏洞，如 SSL/TLS 的实现问题。

---

## **Fiddler 的主要功能**

### **1. 捕获 HTTP/HTTPS 流量**
- Fiddler 可以捕获所有通过代理服务器的 HTTP 和 HTTPS 请求，帮助开发者轻松调试网络问题。
- 支持查看请求的详细信息，例如：
  - URL、Headers、Cookies。
  - 请求体（Request Body）。
  - 响应体（Response Body）。

### **2. 请求修改**
- 支持修改 HTTP 请求，例如：
  - 修改请求头信息。
  - 更改 URL 参数。
  - 编辑请求体内容。

### **3. 自动化测试**
- 支持自定义脚本，通过 **FiddlerScript** 实现复杂的自动化操作。

### **4. 性能测试**
- 模拟不同的网络环境（如慢速网络、丢包等）来测试应用的性能表现。
- 检测大文件的加载时间或页面的响应时间。

### **5. 解密 HTTPS 流量**
- 支持 SSL/TLS 解密，可以捕获和分析加密的 HTTPS 流量。

### **6. 文件导出与共享**
- 支持将网络请求日志导出为文件（如 `.saz` 格式），方便共享或存档。

---

## **Fiddler 的安装与配置**

### **1. 下载与安装**
- 前往 [Fiddler 官方网站](https://www.telerik.com/fiddler) 下载适合的版本。
  - **Fiddler Classic**：适用于 Windows 系统。
  - **Fiddler Everywhere**：跨平台支持 Windows、Mac 和 Linux。
- 按照安装向导完成安装。

### **2. 配置代理**
- 启动 Fiddler 后，它会自动设置为系统默认代理，监听端口为 **8888**。
- 确保浏览器或应用程序的网络请求通过 Fiddler 的代理端口。

### **3. 配置 HTTPS 解密**
1. 打开 **Tools -> Options -> HTTPS**。
2. 勾选 **Decrypt HTTPS Traffic**。
3. 安装 Fiddler 的根证书（首次启用时会自动提示）。
4. 如果调试的是手机流量，需要将手机的网络代理设置为 Fiddler 的 IP 和端口，并安装根证书。

---

## **Fiddler 的界面简介**

### **1. 工具栏**
- 提供快捷访问选项，例如开始/停止捕获流量、清除会话、过滤请求等。

### **2. 请求会话列表**
- 显示捕获的所有网络会话，每条记录包括：
  - **#（编号）**：请求的顺序编号。
  - **Protocol（协议）**：如 HTTP 或 HTTPS。
  - **Host（主机）**：目标服务器的域名。
  - **URL Path**：请求的具体路径。
  - **Result（状态码）**：如 200、404、500 等。
  - **Content Type**：响应的内容类型（如 HTML、JSON、XML）。
  - **Time**：请求的耗时。

### **3. Inspector 面板**
- 提供请求和响应的详细信息，包括：
  - **Headers**：请求和响应的头部信息。
  - **Cookies**：发送和接收的 Cookie。
  - **Raw**：原始请求和响应数据。
  - **JSON/XML**：解析后的结构化数据视图。

### **4. Filters 面板**
- 允许对捕获的会话进行过滤。例如：
  - 仅显示来自特定域名的请求。
  - 隐藏某些类型的请求（如图片或静态资源）。

### **5. Composer 面板**
- 用于手动构建和发送 HTTP 请求。
  - 填写请求的 URL、Method（GET/POST 等）、Headers 和 Body。
  - 点击 **Execute** 发送请求。

---

## **常见操作示例**

### **1. 捕获和查看请求**
1. 启动 Fiddler 并打开浏览器。
2. 在浏览器中访问任意网站，Fiddler 会显示捕获的网络流量。
3. 点击某个请求以查看其详细信息，例如 URL、Headers 和响应内容。

### **2. 修改请求参数**
1. 在 **Inspector** 面板中，找到需要修改的请求。
2. 右键点击并选择 **Edit**。
3. 修改请求的 URL、Headers 或 Body，然后重新发送。

### **3. 模拟慢速网络**
1. 点击 **Rules -> Performance -> Simulate Modem Speeds**。
2. 重新加载页面以查看在慢速网络下的加载效果。

### **4. 导出会话日志**
1. 选择要导出的会话。
2. 点击 **File -> Export Sessions**，选择 `.saz` 格式。
3. 保存到本地以便分析或共享。

### **5. 使用 FiddlerScript 自动化任务**
- 示例脚本：拦截所有请求并在响应中插入自定义头：
  ```javascript
  class Handlers {
      static function OnBeforeResponse(oSession: Session) {
          oSession.oResponse["Custom-Header"] = "Intercepted by Fiddler";
      }
  }
