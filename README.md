# 模板
前不久写了一篇文章[《KindleMate + Anki —— 你不知道的记单词利器》](https://zhuanlan.zhihu.com/p/377358356)分享用KindleMate和Anki背单词的技巧，随着时间推移，我也在不断完善Anki背单词的模板，主要更新有：

1. 添加了大量正则表达式处理释义的格式，以达到样式的美观
1. 修复了翻页时页面闪烁的bug，这个bug困扰了我好几天，最后无意中发现是因为在Anki上用正则表达式替换`[`符号就会导致页面闪烁
1. 如果单词和原型相同，则只显示单词
1. 如未添加音频，音频播放图标则显示为这只小熊 ʕ•́ᴥ•̀ʔっ♡
1. 修改了音标的显示样式，使其更和谐低调
1. 优化了答案显示时的动画特效，使其更流畅舒适
1. 制作了3种模板
   1. 第一种是传统的单卡片模板，先出现单词，后出现释义
   1. 第二种也是单卡片模板，先出现释义，后出现单词
   1. 第三种是双卡片模板，即上面2种单卡片模板的组合

双卡片模板效果如下：

![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1624000414322-1214da79-14d7-4500-bea0-d38f9ef5e3fe.png#clientId=ud25db666-f0ff-4&from=paste&height=564&id=ud1ab488d&margin=%5Bobject%20Object%5D&name=image.png&originHeight=900&originWidth=1014&originalType=binary&ratio=2&size=195455&status=done&style=none&taskId=u3af91e9d-3af9-43ce-8898-109044144a7&width=635)

三种模板均已分享，下载后双击即可安装，请根据需要自行选择

我个人喜欢用第二种模板，即看中文意思回忆英文单词，因为我的单词都是通过阅读积累的，不需要再通过先看单词再看中文意思的方式来再学一遍，通过看中文意思回忆英文单词更能掌握单词的用法也更高效；第三种模板也很好，但是要花费双倍的时间，学习英语不该把过多的时间用在记单词上，所以用第二种就可以了。

下载链接：[https://pan.baidu.com/s/1y0ROMH2_CExjm6LeMeUv0w](https://pan.baidu.com/s/1y0ROMH2_CExjm6LeMeUv0w) 提取码：nsjj 

![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623987722931-8f37ef0a-dd2e-413d-8a37-4291c476ec97.png#clientId=ucd3f0110-f57d-4&from=paste&height=243&id=u95d82878&margin=%5Bobject%20Object%5D&name=image.png&originHeight=260&originWidth=512&originalType=binary&ratio=2&size=67746&status=done&style=none&taskId=u5489197b-e20f-4ed3-bded-3a4ebc1e8bc&width=479)
# 代码

如果你已经安装了模板，想要修改代码，可以点击“**工具**” -> “**管理笔记类型**”

![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623410302310-e336832e-81bc-4b3a-9dbe-1864f4537070.png#clientId=u8cb8e863-5450-4&from=paste&height=373&id=u41cfbd30&margin=%5Bobject%20Object%5D&name=image.png&originHeight=505&originWidth=766&originalType=binary&ratio=2&size=53101&status=done&style=none&taskId=u407c34ad-cb49-4d5b-8625-9c8640a5082&width=566)
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623988364081-eebe30b2-59d8-47eb-bc69-018fdc8bcab3.png#clientId=ucd3f0110-f57d-4&from=paste&height=341&id=ud67f49de&margin=%5Bobject%20Object%5D&name=image.png&originHeight=397&originWidth=599&originalType=binary&ratio=2&size=100861&status=done&style=none&taskId=ud2da7a32-0d12-4c8a-a2e3-125b629f8e1&width=514.5)

如果要修改代码，选中模板后，点击 “**卡片**”，即可看到“正面模板”“背面模板”“样式”三部分的代码。

双卡片模板有卡片1和卡片2，点击上方的“卡片类型”可以切换以修改代码。

![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623988550295-766d2219-43f6-49a6-b68f-51ac5ecff755.png#clientId=ucd3f0110-f57d-4&from=paste&height=391&id=ube889472&margin=%5Bobject%20Object%5D&name=image.png&originHeight=635&originWidth=1086&originalType=binary&ratio=2&size=48784&status=done&style=none&taskId=ufb38952b-880b-465d-9a6d-4aea747bd0c&width=669)

附上我的双卡片模板源代码如下：

单卡片模板(单词-释义)和双卡片模板的卡片一是一样的

单卡片模板(释义-单词)和双卡片模板的卡片二是一样的

**注意**：Anki电脑版不支持ES6语法，比如用let/const声明变量会出现意想不到的bug

## 卡片一
![image.png](https://cdn.nlark.com/yuque/0/2021/png/1753813/1623388740937-2a2398e8-7370-44e4-b750-41d756f47345.png#clientId=u0d9438a7-8a52-4&from=paste&height=96&id=u7906ebd8&margin=%5Bobject%20Object%5D&name=image.png&originHeight=101&originWidth=437&originalType=binary&ratio=2&size=6524&status=done&style=none&taskId=uf4210689-b2de-4347-bd48-1dcff1d5bef&width=417.5)
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
  var word = document.querySelector("#word").innerText.trim()
  var prototype = document.querySelector("#prototype")
  if (word.toLowerCase() === prototype.innerText.toLowerCase()){
    prototype.style.display = "none"
  }
  
  var instance = document.querySelector("#instance")
  if (instance.innerHTML.trim() == '') {
    instance.classList.add("hide")
  } else {
    if (instance.innerHTML.indexOf(`<b><u>${word}</u></b>`) == -1){
        instance.innerHTML = instance.innerHTML.replace(new RegExp(word,"g"), `<b><u>${word}</u></b>`)
    }
  }

  var audio = document.querySelector(".audio")
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
var colorMap = {
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
    var i = div.innerHTML.indexOf('>')
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
var colorMap = {
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

    var div = document.getElementById('paraphrase')
    div.innerHTML = div.innerHTML.replace(/\b[a-z]+\./g, function(symbol) {
        if(colorMap[symbol]) {
          return '<br/><a style="background-color:' + colorMap[symbol] + ';border-radius: 4px; color:white; padding:0 3px;margin-right:5px">'+
          symbol + '</a>';
        }else{
          return symbol;
        }
      }).replace(/(<br\/?>)+/g, '<br/>').replace(/[美英]((?!<a\s).)*\][，\s]?(<br\/?>)?/g, "");
    if(div.innerHTML.indexOf('<br') === 0) {
      var i = div.innerHTML.indexOf('>')
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
  var word = document.querySelector("#word").innerText.trim()
  var prototype = document.querySelector("#prototype")
  if (word.toLowerCase() === prototype.innerText.toLowerCase()){
    prototype.style.display = "none"
  }
  
  var instance = document.querySelector("#instance")
  if (instance.innerHTML.trim() == '') {
    instance.classList.add("hide")
  } else {
    if (instance.innerHTML.indexOf(`<b><u>${word}</u></b>`) == -1){
        instance.innerHTML = instance.innerHTML.replace(new RegExp(word, "g"),`<b><u>${word}</u></b>`)
    }
  }

  var audio = document.querySelector(".audio")
  if (audio.innerHTML === '') {
    audio.innerHTML = 'ʕ•́ᴥ•̀ʔっ♡'
    audio.style.opacity = 1
  }
</script>
```
### 样式
卡片二和卡片一的样式是共用的，不需要修改
