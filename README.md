# wechat

微信接口找茬连萌，我滴法克
你们这帮孩子不能好好干活吗，对得起张晓龙吹的牛逼，你们是一个多么牛逼的团队吗


### [企业付款](http://pay.weixin.qq.com/wiki/doc/api/mch_pay.php?chapter=14_2)

1. 返回参数说好的签名sign呢
2. return_msg device_info 居然是{}说好的string呢

### 不统一的命名规则

1. 在第三榜接口交mch_id,在退款和企业付款交mchid
2. 在第三榜接口交appid,在退款和企业付款交mch_appid
3. 退款接口里没有退款时间
