# 生日特刊 · Birthday Magazine

一本可以翻的生日网页。封面翻开、四个章节、隐藏小游戏、结尾烟花，外加一张「礼物单」页面。

> 本仓库是脱敏模板：**不含任何人名、地名、真实经历、照片与音乐**。照片位置和音乐位置都是示例占位，拿到后按下面三步换成自己的内容即可。

## 文件

| 文件 | 说明 |
| --- | --- |
| `index.html` | 生日杂志：封面 → 第一杯（小游戏）→ 第二杯（照片墙）→ 第三杯（感谢）→ 第四杯（烟花）→ 番外 |
| `gift.html` | 礼物单：A 花 / B 蛋糕 / C 吃饭 / D 自己填，点选盖章 |

两个文件都是**零依赖单文件**（不引外部字体、不引 CDN），双击即可打开。

## 换成自己的内容

**1 · 名字**

`index.html` 里搜「寿星」（封面的 `<h1 class="masthead">`），换成真名；正文里的「你」「她」按语境替换。结尾的署名在 `<span class="sign">`。

**2 · 照片**

把图片放进仓库目录，打开 `index.html` 搜 `const ALBUM`，把每个条目的 `src:""` 填成图片路径：

```js
const ALBUM = {
  hk:     [{src:"photos/trip-01.jpg", caption:"第一段旅程", roll:"TR-01", wide:true}],
  macau:  [{src:"photos/group-01.jpg", caption:"一张合照",   roll:"GR-01"}],
  moments:[{src:"photos/day-01.jpg",   caption:"某个重要场合", roll:"DY-01"}],
  sheShot:[{src:"photos/her-01.jpg",   caption:"最喜欢的一张", roll:"PT-01"}]
};
```

`src` 留空就显示胶片占位框，不会破图。

**3 · 音乐**

把 mp3 放进 `music/`，给 `<audio id="bgm" loop preload="auto">` 补上 `src="music/bgm.mp3"`。标题和歌手在 `#bgmBtn` 里改。

## 结尾照片走马灯

`</script>` 前那个 IIFE 里是 `PHOTO_HINTS`。想放真照片，把该函数改回创建 `<img class="reel-pic">` 并传入路径数组即可（`.reel-pic` 的样式还留在 CSS 里）。

## 交互

- 第一杯：心情选择、场景对话、宣言抽签、彩蛋信
- 第二杯：相册点击放大（灯箱）、键盘可操作
- 第三杯：关键词逐个浮现、「晚安，关灯了」旁注
- 第四杯：夜空烟花、点击任意处放一朵、「再放一次」六连发
- 番外：拎白菜进楼 / 跟服务员搭话，解锁两个角色卡
- 右上角 HUD 记录任务进度

尊重 `prefers-reduced-motion`：开启「减少动态效果」时动画关闭、内容直接显示，走马灯改为手动滑动。

## 授权

[MIT](LICENSE) —— 随意取用、修改、发布，保留版权声明即可。
