## 效果图

![运行效果](./Sources/example.gif)

## 安装

下载项目工程，修改为自己的bundleId

运行主项目JSONSwiftModelApp

再运行JSONSwiftModel

确保没有报错的情况下，选择Products下的JSONSwfitModelApp.app点击右键， 选择show in finder如下图

![](./Sources/showfinder.png)

再将应用移动应用程序即可使用。

### 设置快捷键

可以给插件设置快捷键，快速转换模型

在Xcode -> Preference -> Key Bindings -> Editor Menu For Source Code【或者搜索】就可以找到，如下图

![](./Sources/keybinding.png)

记得双击key下面那个区域才可以编辑，这里我使用的是alt + s 和alt + c 避免与系统的冲突



## 使用

使用的使用，首先要选中需要转换的json,注意不标准的json会报错的哟。仅限单层json，多层json子json需要单独转换

示例json

```javascript
{
  "orderName": "擦护理洗车",
  "decription": "退还到原支付账户",
  "refund": 58,
  "total": 18.2,
  "name": null,
  "detail": {
    "id": 1387329,
    "date": "2018-08-08"
  },
  "tag": [
    "美容洗车",
    "活动",
    "护理"
  ]
}
```

转模结果

```swift
struct <#Model#>: HandyJSON {
    var name: <#NSNull#>?  // 字典为null 需要手动指定类型
    var decription: String?
    var orderName: String?
    var refund: Int?
    var tag: [String]?  // 自动识别数组（如果是基本类型）
    var detail: <#SubModel#>? // 需要再次转子json 模型
    var total: Double?
}
```

![效果图](./Sources/result.png)