# 移动端web开发知识点

## 综述
- 跑在手机端的web页面（H5页面）
- 跨平台
- 基于webview
- 告别ie拥抱webkit
- 更高的适配和性能要求
## 常见移动web适配方法
- 定高，宽度百分比
- flex布局
- Media Query(媒体查询)

#### *Media Query*
```css
@media 媒体类型 and (媒体特性) {
    /* css样式 */
}
```
媒体类型：screen, print...  媒体特性：max-width, min-width....

#### *rem*
> font size of the root element

> 1rem = html的font-size

首先以设计稿的屏幕大小设置html的font-size，然后网页各处（元素尺寸、文字大小）根据此font-size来设置大小，使用rem作为单位，
随后搭配媒体查询或JS，根据屏幕的大小来动态控制html元素的font-size，当html的font-size改变，其他元素的大小也会跟着改变
```css
@media screen and (max-width: 360px) and (min-width: 321px) {
        html {
            font-size: 20px;
        }
    }
@media screen and (max-width: 320px) {
    html {
        font-size: 24px;
    }
}
```
```js
var htmlWidth = document.documentElement.clientWidth || document.body.clientWidth
var htmlDom = document.getElementsByTagName('html')[0]
// 除以多少自行确定
htmlDom.style.fontSize = htmlWidth / 10 + 'px'
// 页面大小改变时，动态改变html的font-size，从而改变页面内容样式
window.addEventListener('resize', ()=> {
    var htmlWidth = document.documentElement.clientWidth || document.body.clientWidth
    htmlDom.style.fontSize = htmlWidth / 10 + 'px'
})
```

