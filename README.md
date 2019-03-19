#Emotion

>一个用于vue的表情输入组件
>https://gitee.com/jiangliyue/vue_expression_input_module.git

>index是使用示例，emotion是组件代码（这里用的是微信表情包的地址，大家可根据需要修改）


####下载安装启动项目查看效果
>####npm install
>####npm run dev
![图像 1.png](https://upload-images.jianshu.io/upload_images/1834649-a3ff8a4277ae69a0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

####Emotion文件夹下Emotion文件说明

>实现原理是根据字段对在线表情包图片进行匹配替换
>代码中 img 标签的地址即为表情图片地址，可自己根据需求替换

```
  mounted () {
    const name = this.$el.innerHTML
    const list = ['微笑', '撇嘴', '色', '发呆', '得意', '流泪', '害羞', '闭嘴', '睡', '大哭', '尴尬', '发怒', '调皮', '呲牙', '惊讶', '难过', '酷', '冷汗', '抓狂', '吐', '偷笑', '可爱', '白眼', '傲慢', '饥饿', '困', '惊恐', '流汗', '憨笑', '大兵', '奋斗', '咒骂', '疑问', '嘘', '晕', '折磨', '衰', '骷髅', '敲打', '再见', '擦汗', '抠鼻', '鼓掌', '糗大了', '坏笑', '左哼哼', '右哼哼', '哈欠', '鄙视', '委屈', '快哭了', '阴险', '亲亲', '吓', '可怜', '菜刀', '西瓜', '啤酒', '篮球', '乒乓', '咖啡', '饭', '猪头', '玫瑰', '凋谢', '示爱', '爱心', '心碎', '蛋糕', '闪电', '炸弹', '刀', '足球', '瓢虫', '便便', '月亮', '太阳', '礼物', '拥抱', '强', '弱', '握手', '胜利', '抱拳', '勾引', '拳头', '差劲', '爱你', 'NO', 'OK', '爱情', '飞吻', '跳跳', '发抖', '怄火', '转圈', '磕头', '回头', '跳绳', '挥手', '激动', '街舞', '献吻', '左太极', '右太极']
    let index = list.indexOf(name)
    let imgHTML = `<img src="https://res.wx.qq.com/mpres/htmledition/images/icon/emotion/${index}.gif">`
    this.$nextTick(() => {
      this.$el.innerHTML = imgHTML
    })
  },
```

####Emotion文件夹下index文件说明

>通过循环列表生成表情包选择框
```
      <div class="emotion-box-line" v-for="(line, i) in list" :key="i" >
        <emotion class="emotion-item" v-for="(item, i) in line" :key="i" @click.native="clickHandler(item)" >{{item}}</emotion>
      </div>
```

####最后需要注意的是表情包评论后保存到后台的是相关字符串，展示时需要还原成图片，具体方法可参考index文件，我这里用了正则匹配转化，还是比较方便的

```
    <div class="text-place">
      <!-- /\#[\u4E00-\u9FA5]{1,3}\;/gi 匹配出含 #XXX; 的字段 -->
      <p v-html="content.replace(/\#[\u4E00-\u9FA5]{1,3}\;/gi, emotion)"></p>
    </div>
```

就这么简单，希望可以帮到有需要的童鞋（￣▽￣）




