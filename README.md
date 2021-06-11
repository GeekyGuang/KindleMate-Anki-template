# 模板
前不久写了一篇文章[《KindleMate + Anki —— 你不知道的记单词利器》](https://www.yuque.com/venivici/grlnzp/yu05oe)分享用KindleMate和Anki背单词的技巧，随着时间推移，我也在不断完善Anki背单词的模板，主要更新有：

1. 添加了大量正则表达式处理释义的格式，以达到样式的美观
1. 修复了翻页时页面闪烁的bug，这个bug困扰了我好几天，最后无意中发现是因为在Anki上用正则表达式替换`[`符号就会导致页面闪烁
1. 如果单词和原型相同，则只显示单词
1. 如未添加音频，音频播放图标则显示为这只小熊 ʕ•́ᴥ•̀ʔっ♡
1. 修改了音标的显示样式，使其更和谐低调
1. 优化了答案显示时的动画特效，使其更流畅舒适
1. 将单面模板升级成了正反两面的模板，实际体验用正反两面的模板背单词效果更好

​

效果预览：
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623411459580-babd15b5-ef02-4be2-bf33-e5f7995212a9.png#clientId=u8cb8e863-5450-4&from=paste&height=653&id=ud5d997bb&margin=%5Bobject%20Object%5D&name=image.png&originHeight=937&originWidth=1056&originalType=binary&ratio=2&size=256662&status=done&style=none&taskId=u3f2dc372-e20f-4273-af39-a75f5090903&width=736)
**单面模板**和**正反双面模板**均已分享，下载后双击即可安装
下载链接：[https://share.weiyun.com/v2nOajjV](https://share.weiyun.com/v2nOajjV) 密码：htnpyr
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623411148424-42de0349-556d-4f14-8538-c14476712514.png#clientId=u8cb8e863-5450-4&from=paste&height=407&id=u10a4d747&margin=%5Bobject%20Object%5D&name=image.png&originHeight=438&originWidth=695&originalType=binary&ratio=2&size=162734&status=done&style=none&taskId=ueada26a6-dd62-493d-970e-a62e7e04029&width=645.5)
# 代码
如果你已经安装了上面2个模板，想要修改代码，可以点击“**工具**” -> “**管理笔记类型**”
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623410302310-e336832e-81bc-4b3a-9dbe-1864f4537070.png#clientId=u8cb8e863-5450-4&from=paste&height=373&id=u41cfbd30&margin=%5Bobject%20Object%5D&name=image.png&originHeight=505&originWidth=766&originalType=binary&ratio=2&size=53101&status=done&style=none&taskId=u407c34ad-cb49-4d5b-8625-9c8640a5082&width=566)
名为KindleMate的是单面模板，KindleMate(and reversed card)是正反双面模板
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623410450811-4a72a3a4-80d9-4dd5-9ee0-23a0d281d873.png#clientId=u8cb8e863-5450-4&from=paste&height=362&id=ub1abb4f0&margin=%5Bobject%20Object%5D&name=image.png&originHeight=574&originWidth=895&originalType=binary&ratio=2&size=118389&status=done&style=none&taskId=uffba1b47-efc8-46d8-8217-1a1a4e9d32f&width=564.5)
如果要修改代码，选中模板后，点击 “**卡片**”，即可看到“正面模板”“背面模板”“样式”三部分的代码。
正反双面卡片有卡片1和卡片2，点击上方的“卡片类型”可以切换以修改代码。
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623410589495-1eb735b2-a9f4-49de-a7bb-2a7a8fd02b2f.png#clientId=u8cb8e863-5450-4&from=paste&height=485&id=u6b1b211e&margin=%5Bobject%20Object%5D&name=image.png&originHeight=749&originWidth=1204&originalType=binary&ratio=2&size=86881&status=done&style=none&taskId=uca6a982b-efd7-46ea-8d3d-c0bf32ca69c&width=779)


附上我的模板源代码如下：
## 卡片一
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623388740937-2a2398e8-7370-44e4-b750-41d756f47345.png#clientId=u0d9438a7-8a52-4&from=paste&height=96&id=u7906ebd8&margin=%5Bobject%20Object%5D&name=image.png&originHeight=101&originWidth=437&originalType=binary&ratio=2&size=6524&status=done&style=none&taskId=uf4210689-b2de-4347-bd48-1dcff1d5bef&width=417.5)
**P.S. **单页面模板代码和卡一模板一样, 复制卡一代码即可
### 正面模板
```html
<!-- 正面区块 -->
<div class="section top">
<div id="front" class="items">
  <span id="word" class="block">{{单词}}</span> 
  <span class="audio block">{{发音}}</span>
  <span id="prototype" class="block">{{原型}}</span> 
</div>
<div id="instance" class="items" >{{用法}}</div>
</div>

<script>
  let word = document.querySelector("#word").innerText.trim()
  let prototype = document.querySelector("#prototype")
  if (word.toLowerCase() === prototype.innerText.toLowerCase()){
    prototype.style.display = "none"
  }
  
  let instance = document.querySelector("#instance")
  if (instance.innerHTML.trim() == '') {
    instance.classList.add("hide")
  } else {
    if (instance.innerHTML.indexOf(`<b><u>${word}</u></b>`) == -1){
        instance.innerHTML = instance.innerHTML.replace(new RegExp(word,"g"), `<b><u>${word}</u></b>`)
    }
  }

  let audio = document.querySelector(".audio")
  if (audio.innerHTML === '') {
    audio.innerHTML = 'ʕ•́ᴥ•̀ʔっ♡'
    audio.style.opacity = 1
  }
</script>
```
### 背面模板
```html
<!-- 背面区块 -->
{{FrontSide}}
<div class="section bounceInUp">
<div id="paraphrase" class="items2">{{释义}}</div>
</div>

<script type="text/javascript">
const colorMap = {
    'n.':'#86c440',
    'a.':'#f8b002',
    'adj.':'#727272',
    'ad.':'#684b9d',
    'adv.':'#684b9d',
    'v.':'#479cdf',
    'vi.':'#3e480d',
    'vt.':'#3e480d',
    'prep.':'#04B7C9',
    'conj.':'#04B7C9',
    'pron.':'#04B7C9',
    'art.':'#04B7C9',
    'num.':'#04B7C9',
    'int.':'#04B7C9',
    'interj.':'#04B7C9',
    'modal.':'#04B7C9',
    'aux.':'#04B7C9',
    'pl.':'#D111D3',
    'abbr.':'#D111D3',
  };
  [].forEach.call(document.querySelectorAll('#paraphrase'), function(div) {
  div.innerHTML = div.innerHTML.replace(/\b[a-z]+\./g, function(symbol) {
    if(colorMap[symbol]) {
      return '<br/><a style="background-color:' + colorMap[symbol] + ';border-radius: 4px; color:white; padding:0 3px;margin-right:5px">'+
      symbol + '</a>';
    } else {
      return symbol;
    }
  }).replace(/\]，/g, ']&nbsp&nbsp')
    .replace(/(<br\/?>)+/g, '<br/>')
    .replace(/[美英]((?!<a\s).)*\]/g, function(symbol){
        symbol = symbol.replace('美', 'us').replace('英','uk').replace(/\]/g, '/').replace(new RegExp('\\[', 'g'), '/');
        return `<span class="soundmark">${symbol}</span>`
    });

  if(div.innerHTML.indexOf('<br') === 0) {
    let i = div.innerHTML.indexOf('>')
    div.innerHTML = div.innerHTML.slice(i+1)
  }
 });

</script>

```
### 样式
```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
  
body,
html {
  background: #eaebee; 
  font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","WenQuanYi Micro Hei",sans-serif;
  line-height: 1.5;
  font-size: 16px;    
}

/*区块全局样式*/
.section {
  border-radius: 13px;                    
  background-color: #fff;                                              
  margin: 10px 2px;
  box-shadow: 0 0 2px rgba(0,0,0,0.3);
}
.top{
  margin-top: 12px;
}

/*区块项全局样式*/
.items{            
  border-top : 1.5px solid rgba(0,0,0, 0.1);   
}
.items, .items2{         
  margin: 0 14px;             
  padding: 10px 0 8px 0;    
}

/*正面字段样式*/
#front{
  border-top: 0px;        
  font-size: 24px; 
  font-family: courier;
  line-height: 1;      
  font-weight: bolder;
  color: #000;       
  display: flex;
  justify-content: center;
  align-items: center;
}

.block {
  display: inline-block;
}

.audio {
  transform: scale(0.5) translateY(3px);
  opacity: 0.1;
}

.hide {
  display: none;
}

.soundmark {
  color: #999;
  font-size: 14px;
}

/*书籍字段样式控制*/  
.book{
  font-size:12px;       
  font-style:italic;
  text-align:right;		 			
  padding-top:6px;
}
.book:before{content:" —— ";}


#prototype{
  font-size  : 18px;       
  text-align : left;       
}

/* 单词在例句中样式 */
#instance u {
 color:  #2cbca1; 
 text-decoration: none;
}

/* 答案显示时动画 */
@keyframes bounceInUp {
  from {
    opacity: 0;
    transform: translate3d(0, 100px, 0);
  }

  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

.bounceInUp {
  animation: bounceInUp 0.3s cubic-bezier(.39,-0.35,.23,1.51);
}
```
## 卡片二
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623388798294-273cb28e-d2a6-4b34-9f1d-8a527f9fa076.png#clientId=u0d9438a7-8a52-4&from=paste&height=151&id=u820383e1&margin=%5Bobject%20Object%5D&name=image.png&originHeight=151&originWidth=461&originalType=binary&ratio=2&size=11588&status=done&style=none&taskId=ue5fa7ec3-14d1-4803-8fea-f8d21354713&width=461)
### 正面模板
```html
<div class="section top">
<div id="paraphrase" class="items2">{{释义}}</div>
</div>

<script type="text/javascript">
const colorMap = {
    'n.':'#86c440',
    'a.':'#f8b002',
    'adj.':'#727272',
    'ad.':'#684b9d',
    'adv.':'#684b9d',
    'v.':'#479cdf',
    'vi.':'#3e480d',
    'vt.':'#3e480d',
    'prep.':'#04B7C9',
    'conj.':'#04B7C9',
    'pron.':'#04B7C9',
    'art.':'#04B7C9',
    'num.':'#04B7C9',
    'int.':'#04B7C9',
    'interj.':'#04B7C9',
    'modal.':'#04B7C9',
    'aux.':'#04B7C9',
    'pl.':'#D111D3',
    'abbr.':'#D111D3',
  };

    let div = document.getElementById('paraphrase')
    div.innerHTML = div.innerHTML.replace(/\b[a-z]+\./g, function(symbol) {
        if(colorMap[symbol]) {
          return '<br/><a style="background-color:' + colorMap[symbol] + ';border-radius: 4px; color:white; padding:0 3px;margin-right:5px">'+
          symbol + '</a>';
        }else{
          return symbol;
        }
      }).replace(/(<br\/?>)+/g, '<br/>').replace(/[美英]((?!<a\s).)*\][，\s]?(<br\/?>)?/g, "");
    if(div.innerHTML.indexOf('<br') === 0) {
      let i = div.innerHTML.indexOf('>')
      div.innerHTML = div.innerHTML.slice(i+1)
    }
</script>

```
### 背面模板
```html
{{FrontSide}}

<div class="section bounceInUp">
<div id="front" class="items">
  <span id="word" class="block">{{单词}}</span> 
  <span class="audio block">{{发音}}</span>
  <span id="prototype" class="block">{{原型}}</span> 
</div>
<div id="instance" class="items" >{{用法}}</div>
</div>

<script>
  let word = document.querySelector("#word").innerText.trim()
  let prototype = document.querySelector("#prototype")
  if (word.toLowerCase() === prototype.innerText.toLowerCase()){
    prototype.style.display = "none"
  }
  
  let instance = document.querySelector("#instance")
  if (instance.innerHTML.trim() == '') {
    instance.classList.add("hide")
  } else {
    if (instance.innerHTML.indexOf(`<b><u>${word}</u></b>`) == -1){
        instance.innerHTML = instance.innerHTML.replace(new RegExp(word, "g"),`<b><u>${word}</u></b>`)
    }
  }

  let audio = document.querySelector(".audio")
  if (audio.innerHTML === '') {
    audio.innerHTML = 'ʕ•́ᴥ•̀ʔっ♡'
    audio.style.opacity = 1
  }
</script>
```
### 样式
卡片二和卡片一的样式是共用的，不需要修改
