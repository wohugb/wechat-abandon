# wechat

微信开发的坑太深，深的你掉进去，连个说话的人都找不到！

你们这帮孩子不能好好干活吗，对得起张晓龙吹的牛逼，你们是一个多么牛逼的团队吗


### [企业付款](http://pay.weixin.qq.com/wiki/doc/api/mch_pay.php?chapter=14_2)

1. 返回参数说好的签名sign呢
2. return_msg device_info 居然是{}说好的string呢
3. 企业支付api,查询订单结果失败,蛋没有失败原因,再次请求支付的时候,尼玛写这么菊花`系统繁忙,请稍后再试.`让我如何理解,如何调试.

### 不统一的命名规则

1. 在第三榜接口交mch_id,在退款和企业付款交mchid
2. 在第三榜接口交appid,在退款和企业付款交mch_appid
3. 退款接口里没有退款时间

### 收货地址共享接口

详细的填坑文档

[微信收货地址共享接口的坑你栽了吗](http://feed.hjue.me/articles/detail/2015-04-18/492466)

### 微信授权登录

授权后居然返回开头0000的code，你大爷的，不知道好多函数处理的时候直接把0干掉吗！

### 微信支付

* 微信取消了支付自动关注的功能,尼玛,支付后的很多后续通知都是通过微信实现的,你现在取消了,后面的怎么做,你不能公号提供了通知功能,然后交易的时候用户有不能便捷关注公号啊,脑子金狮咋想
* 经过一小孩验证少于5元将不能自动关注

### 关于微信小店接口

没有购买接口，如果基于微信小店进行二次开发，把微信小店作为一些基础管理，而在次基础上开发更适用的社交功能，将不能实现

### 微信第三方后台事件推送

他是不问青红皂白只要授权了就给你推啊,管你跟这事件有没有关系,最近做了个第三方结果一个做卡圈营销的授权了,差点把服务器搞挂了!

### 再来一条微信模板的问题

1. 模板的逻辑只有新建的时候才能获取到id
2. 如果模板已经存在，就提示错误也获取不到id
3. 这是一个多么该死的逻辑
4. 获取模板列表里居然没有`template_id_short`字段，你让我如何比对啊

### 常见错误码

* template conflict with industry hint
* 行业模板冲突

* template num exceeds limit
* 模板数量超过上限

### 查询代金券批次信息的文档错误

#### 签名	sign 不错在

#### 时间格式说明和输出不匹配

```
生效开始时间	begin_time	是	1943787483	String	格式为yyyyMMddhhmmss，如2009年12月27日9点10分10秒表示为20091227091010。
生效结束时间	end_time	是	1943787490	String	格式为yyyyMMddhhmmss，如2009年12月27日9点10分10秒表示为20091227091010。
创建时间	create_time	是	1943787420	String	格式为yyyyMMddhhmmss，如2009年12月27日9点10分10秒表示为20091227091010。
```

### 关于卡券的建议 

试用了一下卡券,限制太多,不太实用,也不适合第三方开发,你们所有的接口都是在已有的功能开放,没有多大意思,既然你们后台都可以做,而且做的一定会比普通开发者要好,所以那些接口对于普通开发者就是鸡肋.

一般普通小开发者要的当然是有个性的东西,也就是自定义性要强,你们的开全只支持群发投递,而且还有个数限制,太死板,无法完成一些个性化的需求.

比如,我有个平台,想让组织者完成一次活动组织就给他发送卡券,这样卡券投递可能就是自动和单一和多次,如果使用你们平台虽然也能通过openid群发,而且还只能图文,而用户只能最多接受四次,这就麻烦了,以后的活动都收不到卡券了.


### 龙哥是因为你们团队人多没法协调吗？

你说你都允许公号可以授权给多个应用，回头你用限制消息模板的行业，每个应用都有独自的行业，而每个公号不一定使用一个行业的应用，比如水果店，它既需要电子商务的应用，又需要进销存的软件应用，还可能是电子称的硬件应用，你现在把消息模板给封死了，你说让他砸选。

龙哥你何必这么麻烦，吧分类去掉限制个数不就可以了吗@张小龙

### 龙哥每次你的小弟给返回一些莫名其妙的错误，还无从查找，还找不到客服的时候，我就特别想您

您能告诉我公号授权后，用授权码换token给的错误提示 `user limited` 是啥意思嘛？

ps: 每当这个时候就感觉龙哥就是救世主，客户就是撒旦！可是啥时候见过主啊？恶魔可是每天都有的！

### 龙哥你细胞分裂后就互相开锁了

这里需要【中控中心】(http://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421140183&token=&lang=zh_CN)，然后第三方应用需要【白名单】(https://open.weixin.qq.com)，哦草了，我能把我的应用授权给其他应用吗，白痴啊，有能呆你做个中控中心啊，你脱裤子放屁，不嫌费事啊

### 门店的坑

最近遇到的门店组件添加完毕，可以申请门店，但是第三方不能调用门店列表，后来解决的方法是申请卡券后就可以使用门店，不懂轻重的逻辑

### 临时二维码时为32位非0整型

[坑主在这里](http://blog.csdn.net/t244387066/article/details/51462558)

`其实是指 二进制的位数是32位，而不是10进制的位数。~~~`
