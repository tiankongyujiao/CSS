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
    flex-shrink: 0;
    flex-grow: 0;
}

.wrap>div:last-child {
    margin-right: 0;
    flex-shrink: 0;
    flex-grow: 0;
}
```
设置 ** flex-basis: 20px; ** 每个子元素，然后给两边的div设置 ** flex-shrink: 0; flex-grow: 0; ** 这样就能实现两边宽度固定，中间自适应。
