### flex弹性盒子布局

1. 两边宽度固定，中间自适应布局方法：
```
// html
<div class="wrap">
    <div class="f">1</div>
    <div class="s">2</div>
    <div class="t">3</div>
</div>

// css
body {
    margin: 0;
    padding: 0;
}
.wrap {
    width: 100vw;
    height: 200px;
    border: 1px solid #f40;
    display: flex;
    display: -webkit-flex;
    align-items: center;
    justify-content: center;
}

.wrap>div {
    flex: 1;
    width: 500px;
    flex-shrink: 1;
    flex-basis: 20px;
    text-align: center;
}

.wrap>div:first-child {
    flex-shrink: 0; // 空间小时不缩小
    flex-grow: 0; // 空间大时不放大
}

.wrap>div:last-child {
    margin-right: 0;
    flex-shrink: 0; // 空间小时不缩小
    flex-grow: 0; // 空间大时不放大
}
```
设置 **flex-basis: 20px;** 每个子元素，然后给两边的div设置 **flex-shrink: 0; flex-grow: 0;** 这样就能实现两边宽度固定，中间自适应。  
想要固定的宽度 **flex-shrink: 0; flex-grow: 0;** 要和 **flex-basis: 20px;** 搭配使用。

2. 实现垂直方向上的自适应浏览器窗口大小，左边11，12，13每个item高度平均分割窗口高度，右边31，32，33上面的21和32固定高度，33高度随窗口高度变化。
```
// html
<div class="wrap">
    <div class="f">
        <div>11</div>
        <div>12</div>
        <div>13</div>
    </div>
    <div class="s">2</div>
    <div class="t">
        <div>31</div>
        <div class="s">32</div>
        <div>33</div>
    </div>
</div>
// css
body {
    margin: 0;
    padding: 0;
}
.wrap {
    width: 100vw;
    height: 100vh;
    border: 1px solid #f40;
    display: flex;
    display: -webkit-flex;
    align-items: center;
    justify-content: center;
}

.wrap>div {
    flex: 1;
    width: 500px;
    height: 100vh;
    flex-shrink: 1; // 默认也是1
    flex-basis: 200px; // 默认两边宽度是200，因为第一个和最后一个div设置了flex-shrink: 0;和flex-grow: 0;
    text-align: center;
    display: flex; // 设置这个使下一级的div具有flex的盒模型
    flex-direction: column; // 垂直布局，从上到下
}

.wrap>div>div {
    flex: 1;
}

.wrap>div:first-child {
    flex-shrink: 0; // 空间小时不缩小
    flex-grow: 0; // 空间大时不放大
    background: #f40;
}

.wrap>div:last-child {
    margin-right: 0;
    flex-shrink: 0; // 空间小时不缩小
    flex-grow: 0; // 空间大时不放大
    background: #f40;
}

.wrap>div.t>div {
    flex-basis: 100px;
}

.wrap>div.t>div:first-child {
    flex-grow: 0;
    flex-shrink: 0;
}

.wrap>div.t>div.s {
    flex-grow: 0;
    flex-shrink: 0;
}
```


