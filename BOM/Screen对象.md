# Screen对象

## CONTENT

### Screen 对象

Screen 对象包含有关客户端显示屏幕的信息。

![Note](https://upload-images.jianshu.io/upload_images/7728717-b092c1695c8a3b2d.gif?imageMogr2/auto-orient/strip) **注意：** 没有应用于 screen 对象的公开标准，不过所有浏览器都支持该对象。

* * *

### Screen 对象属性

| 属性 | 说明 |
|-|-|
| availHeight | 返回屏幕的高度（不包括Windows任务栏） |
| availWidth | 返回屏幕的宽度（不包括Windows任务栏） |
| height | 返回屏幕的总高度 |
| width | 返回屏幕的总宽度 |
| colorDepth | 返回目标设备或缓冲器上的调色板的比特深度 |
| pixelDepth | 返回屏幕的颜色分辨率（每象素的位数） |

* * *

## Screen对象属性

```js
console.log("可用高度: " + screen.availHeight);
// 可用高度: 1040
console.log("可用宽度: " + screen.availWidth);
// 可用宽度: 1920
console.log("总高度: " + screen.height);
// 总高度: 1080
console.log("总宽度: " + screen.width);
// 总宽度: 1920
console.log("颜色深度: " + screen.colorDepth);
// 颜色深度: 24
console.log("颜色分辨率: " + screen.pixelDepth);
// 颜色分辨率: 24
```

**定义和用法**

`availHeight` 属性声明了显示浏览器的屏幕的可用高度，以像素计。在 Windows 这样的操作系统中，这个可用高度不包括分配给半永久特性（如屏幕底部的任务栏）的垂直空间。

`availWidth` 属性声明了显示浏览器的屏幕的可用宽度，以像素计。在 Windows 这样的操作系统中，这个可用高度不包括分配给半永久特性（如屏幕底部的任务栏）的垂直空间。

`height` 属性声明了显示浏览器的屏幕的高度，以像素计。

`width` 属性声明了显示浏览器的屏幕的宽度，以像素计。

`colorDepth` 属性返回目标设备或缓冲器上的调色板的比特深度。

`pixelDepth` 属性返回显示屏幕的颜色分辨率（比特每像素）。

**语法**

`screen.availHeight`

`screen.availWidth`

`screen.height`

`screen.width`

`screen.colorDepth`

`screen.pixelDepth`
