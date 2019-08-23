# HTMLDOM元素对象

## HTML DOM 节点

在 HTML DOM (Document Object Model) 中, 每个东西都是 **节点**:

*   文档本身就是一个文档对象
*   所有 HTML 元素都是元素节点
*   所有 HTML 属性都是属性节点
*   插入到 HTML 元素文本是文本节点
*   注释是注释节点

* * *

## 元素对象

在 HTML DOM 中, **元素对象**代表着一个 HTML 元素。

元素对象 的 **子节点**可以是, 可以是元素节点，文本节点，注释节点。

**NodeList 对象** 代表了节点列表，类似于 HTML元素的子节点集合。

元素可以有属性。属性属于属性节点（查看属性对象一章节）。

* * *

## 浏览器支持

![Internet Explorer](https://upload-images.jianshu.io/upload_images/7728717-0ede7464e44b96fe.gif?imageMogr2/auto-orient/strip "Internet Explorer")
![Firefox](https://upload-images.jianshu.io/upload_images/7728717-cb6a6aa2698dd92c.gif?imageMogr2/auto-orient/strip "Firefox")
![Opera](https://upload-images.jianshu.io/upload_images/7728717-f63313c4119481ac.gif?imageMogr2/auto-orient/strip "Opera")
![Google Chrome](https://upload-images.jianshu.io/upload_images/7728717-aad302296dc57b72.gif?imageMogr2/auto-orient/strip "Google Chrome")
![Safari](https://upload-images.jianshu.io/upload_images/7728717-6c41ce16dccfc147.gif?imageMogr2/auto-orient/strip "Safari")

所有主流浏览器都支持 元素对象 和 NodeList 对象。.

* * *

## CONTENT

以下 **属性和方法** 可适用于所有 HTML 元素：

| 属性 / 方法 | 描述 |
|-|-|
|以下链接不在本文章中|-|
| [*element*.accessKey](https://www.runoob.com/jsref/prop-html-accesskey.html) | 设置或返回accesskey一个元素 |
| [*element*.addEventListener()](https://www.runoob.com/jsref/met-element-addeventlistener.html) | 向指定元素添加事件句柄 |
| [*element*.appendChild()](https://www.runoob.com/jsref/met-node-appendchild.html) | 为元素添加一个新的子元素 |
| [*element*.attributes](https://www.runoob.com/jsref/prop-node-attributes.html) | 返回一个元素的属性数组 |
| [*element*.childNodes](https://www.runoob.com/jsref/prop-node-childnodes.html) | 返回元素的一个子节点的数组 |
| [*element*.children](https://www.runoob.com/jsref/prop-element-children.html) | 返回元素的子元素的集合 |
| [*element*.classList](https://www.runoob.com/jsref/prop-element-classList.html) | 返回元素的类名，作为 DOMTokenList 对象。 |
| [*element*.className](https://www.runoob.com/jsref/prop-html-classname.html) | 设置或返回元素的class属性 |
| *element*.clientHeight | 在页面上返回内容的可视高度（不包括边框，边距或滚动条） |
| *element*.clientWidth | 在页面上返回内容的可视宽度（不包括边框，边距或滚动条） |
| [*element*.cloneNode()](https://www.runoob.com/jsref/met-node-clonenode.html) | 克隆某个元素 |
| [*element*.compareDocumentPosition()](https://www.runoob.com/jsref/met-node-comparedocumentposition.html) | 比较两个元素的文档位置。 |
| [*element*.contentEditable](https://www.runoob.com/jsref/prop-html-contenteditable.html) | 设置或返回元素的内容是否可编辑 |
| [*element*.dir](https://www.runoob.com/jsref/prop-html-dir.html) | 设置或返回一个元素中的文本方向 |
| [*element*.firstChild](https://www.runoob.com/jsref/prop-node-firstchild.html) | 返回元素的第一个子节点 |
| [*element*.focus()](https://www.runoob.com/jsref/met-html-focus.html) | 设置文档或元素获取焦点 |
| [*element*.getAttribute()](https://www.runoob.com/jsref/met-element-getattribute.html) | 返回指定元素的属性值 |
| [*element*.getAttributeNode()](https://www.runoob.com/jsref/met-element-getattributenode.html) | 返回指定属性节点 |
| [*element*.getElementsByTagName()](https://www.runoob.com/jsref/met-element-getelementsbytagname.html) | 返回指定标签名的所有子元素集合。 |
| [*element*. getElementsByClassName()](https://www.runoob.com/jsref/met-element-getelementsbyclassname.html) | 返回文档中所有指定类名的元素集合，作为 NodeList 对象。 |
| *element*.getFeature() | 返回指定特征的执行APIs对象。 |
| *element*.getUserData() | 返回一个元素中关联键值的对象。 |
| [*element*.hasAttribute()](https://www.runoob.com/jsref/met-element-hasattribute.html) | 如果元素中存在指定的属性返回 true，否则返回false。 |
| [*element*.hasAttributes()](https://www.runoob.com/jsref/met-node-hasattributes.html) | 如果元素有任何属性返回true，否则返回false。 |
| [*element*.hasChildNodes()](https://www.runoob.com/jsref/met-node-haschildnodes.html) | 返回一个元素是否具有任何子元素 |
| [*element*.hasFocus()](https://www.runoob.com/jsref/met-document-hasfocus.html) | 返回布尔值，检测文档或元素是否获取焦点 |
| [*element*.id](https://www.runoob.com/jsref/prop-html-id.html) | 设置或者返回元素的 id。 |
| [*element*.innerHTML](https://www.runoob.com/jsref/prop-html-innerhtml.html) | 设置或者返回元素的内容。 |
| [*element*.insertBefore()](https://www.runoob.com/jsref/met-node-insertbefore.html) | 现有的子元素之前插入一个新的子元素 |
| [*element*.isContentEditable](https://www.runoob.com/jsref/prop-html-iscontenteditable.html) | 如果元素内容可编辑返回 true，否则返回false |
| [*element*.isDefaultNamespace()](https://www.runoob.com/jsref/met-node-isdefaultnamespace.html) | 如果指定了namespaceURI 返回 true，否则返回 false。 |
| [*element*.isEqualNode()](https://www.runoob.com/jsref/met-node-isequalnode.html) | 检查两个元素是否相等 |
| [*element*.isSameNode()](https://www.runoob.com/jsref/met-node-issamenode.html) | 检查两个元素所有有相同节点。 |
| [*element*.isSupported()](https://www.runoob.com/jsref/met-node-issupported.html) | 如果在元素中支持指定特征返回 true。 |
| [*element*.lang](https://www.runoob.com/jsref/prop-html-lang.html) | 设置或者返回一个元素的语言。 |
| [*element*.lastChild](https://www.runoob.com/jsref/prop-node-lastchild.html) | 返回的最后一个子节点 |
| [*element*.namespaceURI](https://www.runoob.com/jsref/prop-node-namespaceuri.html) | 返回命名空间的 URI。 |
| [*element*.nextSibling](https://www.runoob.com/jsref/prop-node-nextsibling.html) | 返回该元素紧跟的一个节点 |
| [*element*.nextElementSibling](https://www.runoob.com/jsref/prop-element-nextelementsibling.html) | 返回指定元素之后的下一个兄弟元素（相同节点树层中的下一个元素节点）。 |
| [*element*.nodeName](https://www.runoob.com/jsref/prop-node-nodename.html) | 返回元素的标记名（大写） |
| [*element*.nodeType](https://www.runoob.com/jsref/prop-node-nodetype.html) | 返回元素的节点类型 |
| [*element*.nodeValue](https://www.runoob.com/jsref/prop-node-nodevalue.html) | 返回元素的节点值 |
| [*element*.normalize()](https://www.runoob.com/jsref/met-node-normalize.html) | 使得此成为一个"normal"的形式，其中只有结构（如元素，注释，处理指令，CDATA节和实体引用）隔开Text节点，即元素（包括属性）下面的所有文本节点，既没有相邻的文本节点也没有空的文本节点 |
| *element*.offsetHeight | 返回任何一个元素的高度包括边框和填充，但不是边距 |
| *element*.offsetWidth | 返回元素的宽度，包括边框和填充，但不是边距 |
| *element*.offsetLeft | 返回当前元素的相对水平偏移位置的偏移容器 |
| *element*.offsetParent | 返回元素的偏移容器 |
| *element*.offsetTop | 返回当前元素的相对垂直偏移位置的偏移容器 |
| [*element*.ownerDocument](https://www.runoob.com/jsref/prop-node-ownerdocument.html) | 返回元素的根元素（文档对象） |
| [*element*.parentNode](https://www.runoob.com/jsref/prop-node-parentnode.html) | 返回元素的父节点 |
| [*element*.previousSibling](https://www.runoob.com/jsref/prop-node-previoussibling.html) | 返回某个元素紧接之前元素 |
| [*element*.previousElementSibling](https://www.runoob.com/jsref/prop-element-previouselementsibling.html) | 返回指定元素的前一个兄弟元素（相同节点树层中的前一个元素节点）。 |
| [*element*.querySelector()](https://www.runoob.com/jsref/met-element-queryselector.html) | 返回匹配指定 CSS 选择器元素的第一个子元素 |
| document.querySelectorAll() | 返回匹配指定 CSS 选择器元素的所有子元素节点列表 |
| [*element*.removeAttribute()](https://www.runoob.com/jsref/met-element-removeattribute.html) | 从元素中删除指定的属性 |
| [*element*.removeAttributeNode()](https://www.runoob.com/jsref/met-element-removeattributenode.html) | 删除指定属性节点并返回移除后的节点。 |
| [*element*.removeChild()](https://www.runoob.com/jsref/met-node-removechild.html) | 删除一个子元素 |
| [*element*.removeEventListener()](https://www.runoob.com/jsref/met-element-removeeventlistener.html) | 移除由 addEventListener() 方法添加的事件句柄 |
| [*element*.replaceChild()](https://www.runoob.com/jsref/met-node-replacechild.html) | 替换一个子元素 |
| *element*.scrollHeight | 返回整个元素的高度（包括带滚动条的隐蔽的地方） |
| *element*.scrollLeft | 返回当前视图中的实际元素的左边缘和左边缘之间的距离 |
| *element*.scrollTop | 返回当前视图中的实际元素的顶部边缘和顶部边缘之间的距离 |
| *element*.scrollWidth | 返回元素的整个宽度（包括带滚动条的隐蔽的地方） |
| [*element*.setAttribute()](https://www.runoob.com/jsref/met-element-setattribute.html) | 设置或者改变指定属性并指定值。 |
| [*element*.setAttributeNode()](https://www.runoob.com/jsref/met-element-setattributenode.html) | 设置或者改变指定属性节点。 |
| *element*.setIdAttribute() |  |
| *element*.setIdAttributeNode() |  |
| *element*.setUserData() | 在元素中为指定键值关联对象。 |
| *element*.style | 设置或返回元素的样式属性 |
| [*element*.tabIndex](https://www.runoob.com/jsref/prop-html-tabindex.html) | 设置或返回元素的标签顺序。 |
| [*element*.tagName](https://www.runoob.com/jsref/prop-element-tagname.html) | 作为一个字符串返回某个元素的标记名（大写） |
| [*element*.textContent](https://www.runoob.com/jsref/prop-node-textcontent.html) | 设置或返回一个节点和它的文本内容 |
| [*element*.title](https://www.runoob.com/jsref/prop-html-title.html) | 设置或返回元素的title属性 |
| *element*.toString() | 一个元素转换成字符串 |
| [*nodelist*.item()](https://www.runoob.com/jsref/met-nodelist-item.html) | 返回某个元素基于文档树的索引 |
| [*nodelist*.length](https://www.runoob.com/jsref/prop-nodelist-length.html) | 返回节点列表的节点数目。 |

