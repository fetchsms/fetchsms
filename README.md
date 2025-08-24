# 📱 手机号短信接码API - （光年号GN号）

> 一个在线收取手机号码短信的 API 平台，提供高度可定制的短信收取接口。  
> 项目目标：为开发者、企业、跨境业务等提供 **稳定、安全、灵活** 的短信接收服务。  

---

## 🚀 项目简介

**手机号短信接码API** 是一个在线收取短信的服务平台，用户可通过光年号（[gnhao.com](https://gnhao.com/)） API 接口实时获取目标手机号码的短信内容。  
该项目特别适合需要 **验证码接收**、**账号注册**、**跨境业务通信**、**自动化测试** 的开发和企业用户。  

---

## ✨ 功能特点

- 📩 **在线收取短信**：实时获取指定手机号码收到的短信内容  
- 🔑 **高度可定制**：支持 API 接口调用，可灵活接入业务系统  
- 🌍 **全球覆盖**：支持多个国家和地区手机号  
- 🔒 **安全可靠**：短信加密存储，保证用户数据安全  
- ⚡ **快速响应**：5-30 秒内轮询获取最新短信内容  
- 🔄 **转发支持**：可选配置，自动转发短信到邮箱或其他手机号  

---

## 📖 使用场景

- ✅ 网站/APP 账号注册验证码接收  
- ✅ 跨境电商、外贸业务手机验证  
- ✅ 软件测试、自动化脚本收取短信  
- ✅ 临时号码收码，保障隐私与安全  

---

## 🛠 API 接口说明

### 获取短信内容

👌我帮你基于光年号的 **获取短信内容 API 文档**，写几个常见语言的示例代码（`Python` / `PHP` / `Node.js`），你可以直接放到 GitHub 里作为示例。

---

## Python 示例

```python
import requests

url = "https://gnhao.com/index/api/get_sms_v1"

payload = {
    "app_key": "your_app_key_here",   # 替换为你的API密钥
    "phone": "7123456789"             # 可选，英国号码10位数字，不带国家码
}

try:
    response = requests.post(url, data=payload, timeout=10)
    result = response.json()

    if result.get("code") == 200:
        sms = result.get("data", {})
        print("📩 收信号码:", sms.get("phone"))
        print("👤 发信人:", sms.get("sender"))
        print("🏷️ 发信人名称:", sms.get("sender_name"))
        print("📝 短信内容:", sms.get("content"))
        print("⏰ 发送时间:", sms.get("send_time"))
    else:
        print("❌ 错误:", result.get("message"))

except Exception as e:
    print("请求失败:", str(e))
```

---

## PHP 示例

```php
<?php
$url = "https://gnhao.com/index/api/get_sms_v1";

$postData = [
    "app_key" => "your_app_key_here",   // 替换为你的API密钥
    "phone"   => "7123456789"           // 可选参数，英国号码10位数字
];

$options = [
    "http" => [
        "method"  => "POST",
        "header"  => "Content-type: application/x-www-form-urlencoded",
        "content" => http_build_query($postData),
        "timeout" => 10
    ]
];

$context = stream_context_create($options);
$response = file_get_contents($url, false, $context);

if ($response !== false) {
    $result = json_decode($response, true);
    if ($result["code"] == 200) {
        $sms = $result["data"];
        echo "📩 收信号码: " . $sms["phone"] . PHP_EOL;
        echo "👤 发信人: " . $sms["sender"] . PHP_EOL;
        echo "🏷️ 发信人名称: " . $sms["sender_name"] . PHP_EOL;
        echo "📝 短信内容: " . $sms["content"] . PHP_EOL;
        echo "⏰ 发送时间: " . $sms["send_time"] . PHP_EOL;
    } else {
        echo "❌ 错误: " . $result["message"];
    }
} else {
    echo "请求失败";
}
?>
```

---

## Node.js 示例

```javascript
const axios = require("axios");

const url = "https://gnhao.com/index/api/get_sms_v1";

const payload = {
  app_key: "your_app_key_here",  // 替换为你的API密钥
  phone: "7123456789"            // 可选参数，英国号码10位数字
};

axios.post(url, new URLSearchParams(payload).toString(), {
  headers: { "Content-Type": "application/x-www-form-urlencoded" }
})
.then(res => {
  const result = res.data;
  if (result.code === 200) {
    const sms = result.data;
    console.log("📩 收信号码:", sms.phone);
    console.log("👤 发信人:", sms.sender);
    console.log("🏷️ 发信人名称:", sms.sender_name);
    console.log("📝 短信内容:", sms.content);
    console.log("⏰ 发送时间:", sms.send_time);
  } else {
    console.log("❌ 错误:", result.message);
  }
})
.catch(err => {
  console.error("请求失败:", err.message);
});
```

---

✅ 上面三个示例都实现了 **调用 API → 解析返回结果 → 打印短信内容** 的流程。

