 ### 活动状态码
 
 
```
UNLOGIN: -1,
START   : 3,
NOTSTART: -5,
GAMEOVER: -6,
RECHARGE :-10

```



### 获取礼包码

### interface  

_zt._ztUrl + "-ajaxGetCode"

### descrition 

获取礼包接口

### method 

POST

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是
id | num | 中奖id,当抽到集合礼包时要传 | 否  
pid | num | 礼包id,当抽到集合礼包时要传相应游戏的pid | 是



### return 


```
{
    "status":1,
    "msg":"抽奖成功",
    "data":{
        "prize":1,   //奖品id
        "prizeName":"游戏礼包（普通）",  //奖品名
        "lastTimes":900,    //剩余抽奖次数
        "kind" : 2 ,    //礼包类型  kind=1礼包码礼包 kind=2不要用户信息的礼包  kind=3 需要用户填写信息的礼包  kind=4 礼包集合
        
        //如果是礼包码礼包 kind = 1  
        "code":24332432
        
    }
}
```


### 兑换礼包接口

### interface  

_zt._ztUrl + "-ajaxExchange"

### descrition 

兑换礼包接口

### method 

POST

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是
code | string | 如果是礼包码兑换则要传礼包码 | 否  
pid | num | xxxx | 否  


### return 

```
{
    "status":1,
    "msg":"兑换成功！",
    "data":{
        "pid":22222,
        "prizeName":"咸鱼背包",
        "kind" : 2 ,    //礼包类型  kind=1礼包码礼包 kind=2不要用户信息的礼包  kind=3 需要用户填写信息的礼包  kind=4 礼包集合
        
        //如果是礼包码礼包 kind = 1  
        "code":24332432
    }
}
```


### 抽奖

### interface  

_zt._ztUrl + "-ajaxLottery-"

### descrition 

抽奖接口 单次抽奖 list是奖品信息的对象 连抽 list是奖品数组

### method 

POST

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是
time | num | xx | 是



### return 


```
{
    "status":1,
    "msg":"抽奖成功",
    "data":{
        "prize":1,   //奖品id   当抽中集合礼包 要根据这个pid去映射相应游戏的pid
        "prizeName":"游戏礼包（普通）",  //奖品名
        "lastTimes":900,    //剩余抽奖次数
        "kind" : 2 ,    //礼包类型  kind=1礼包码礼包 kind=2不要用户信息的礼包  kind=3 需要用户填写信息的礼包  kind=4 礼包集合
        
        //如果是礼包码礼包 kind = 1  
        "code":24332432
        
    }
}
```



### 获取礼包列表

### interface  

_zt._ztUrl + "-ajaxGetMyPrizes"

### descrition 

获取我的奖品列表

### method 

GET

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是
p | num | 获取列表的页数 | 是



### return 


```
{
    "status": 1,
    "msg": "奖品信息",
    "data": {
        "count": 32,//总个数
        "pagecount": 4, //总页数
        "list": [
            {
                //基本字段
                "id": "1",//中奖id
                "prize": "0",//礼包id
                "prizeName": "XXXXX1",//礼包名称
                "kind": 1,//礼包类型 kind=1礼包码礼包 kind=2不要用户信息的礼包  kind=3 需要用户填写信息的礼包  kind=4 礼包集合

                //如果是礼包 kind = 1
                "code": "1267645584_0",//礼包

                //如果是需要用户填写信息的奖品 如实物 kink = 3
                "uinfo": 1, // 是否已经填写了用户信息 0未填写 1已填写
                "uname": "xxxx",//用户姓名
                "uphone": "110",//用户联系方式
                "uaddress": "xxxxxx",//用户地址

                //游戏url
                "url":"http:\/\/ssjj.4399.com"
            },
        }
    }
}
```


### 填写实物礼包信息

### interface  

_zt._ztUrl + "-ajaxWriteUserInfo

### descrition 

中奖实物后，填写用户信息接口

### method 

POST

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是
pid | num | 礼包id 第一次填写要传 | 否  
id | num |中奖id 第一次填写要传 | 否
uaddress | string | 地址 | 否
uname | string | 姓名 | 否
uphone | string | 手机号码 | 否


### return 


```
{
    "status":1,
    "msg":"报名成功",
    "data":{}
}
```



### 获取签到数据

### interface  

_zt._ztUrl + "-ajaxGetSignTbl"

### descrition 

获取签到日期

### method 

GET

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是
month | num | 月份 | 是



### return 


```
{
    "status": 1,
    "msg": "签到数据！",
    "data": {
        "tbl": [
            {
                "n": "5",     //月
                "j": "1",     //日
                "Ymd": "20170501",  //日期
                "cur": 0,     //签到状态  0未签到 1已签到
                "type": 1     //当天的活动  1比赛 2直播
            },
            {
                "n": "5",
                "j": "2",
                "Ymd": "20170502",
                "cur": 1
            },
            {
                "n": "5",
                "j": "3",
                "Ymd": "20170503",
                "cur": 0
            }
        }
    }
}
```




### 签到

### interface  

_zt._ztUrl + "-ajaxSign"

### descrition 

签到

### method 

GET

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是



### return 


```
{
    "status":1,
    "msg":"签到成功",
    "data":{
        "num":8,    
        "n":"5",    //月
        "j":"3",     //日
        "Ymd":"20170503",   //日期
        "lastTimes":888890  //剩余抽奖次数
    }
}
```


### 打开宝箱接口

### interface  

_zt._ztUrl + "-ajaxGetCode"

### descrition 

倒计时开宝箱

### method 

POST

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是
bxId | num | 宝箱id，后一次宝箱id由前一次宝箱接口返回，当id为0时即没有宝箱了 | 否  
flag | num | 加密串 | 是
yx | string | 当前游戏 | 是


### return 


```
{
    "status":1,
    "msg":"领取成功，请及时使用夺宝次数",
    "data":{
        "minutes":"0.1",    //下一个宝箱倒计时时间
        "bxId":23,          //下一个宝箱id
        "time":1499750100,  
        "flag":"0d95b3c03b237f0e0c61a6c95acc32ca"  //下一个宝箱加密串
    }
}
```


### 直播接口

### interface  

_zt._ztUrl+"-ajaxGetZbList"

### descrition 

获取直播数据 

### method 

GET

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是

### return 


```
{
    "status": 1,
    "msg": "直播信息",
    "data": {
        "zbStatus": {
            "status": 1,
            "freshBlank": 7,            //请求接口时间间隔
            "yxid": "1",                //游戏id
            "today": "20180622",
            "defPt": 0,                 //默认直播平台索引
            "zbId": 1,                  //直播id
            "start": 1529575560,        //直播开始时间
            "end": 1532184600,          //直播结束时间
            "zbUrl": "./djs18-ssjj",
            
            "bxId": 1,                  //宝箱id
            "minutes": "1",             //宝箱开启倒计时
            "time": 1529638984,
            "flag": "02c8476e2ca4babc65964df7381cd6b5",  //宝箱开启加密串
            "wapPtList": [
                {
                    "name": "游拍",
                    "type": "yp",
                    "ypWap": null
                }
            ],
            "ptList": [                //直播平台列表
                {
                    "name": "游拍",           //直播平台名称
                    "type": "yp",             //直播平台类型
                    "url": "http://mapi.4399youpai.com/live/detail/frame/330511.html?source=dj&ishowgift=0&ishowchat=0&iswidauto=1"    //直播平台地址
                },
                {
                    "name": "嗯嗯啊啦啦啦啦",
                    "type": "yp",
                    "url": "http://mapi.4399youpai.com/live/detail/frame/81185.html?source=dj&ishowgift=0&ishowchat=0&iswidauto=1"
                },
                {
                    "name": "嗯嗯啊啦啦啦啦",
                    "type": "yp",
                    "url": "http://mapi.4399youpai.com/live/detail/frame/81185.html?source=dj&ishowgift=0&ishowchat=0&iswidauto=1"
                }
            ],
            "defYx": 0,            //默认当前游戏id
            "wapImg": "http://f1.img4399.com/dj~2017/11/23/09_DnGSxA0vWh.239x137.jpg"
        },
        "zbList": [                 //直播列表
            {
                "id": "3",          //直播id
                "yxid": "4",        //游戏id
                "stage": "0",       //直播进行的阶段 0：淘汰赛 1：小组赛
                "start": "20180623 18:00",   //直播开始时间
                "end": "20180623 21:00",     //直播开始时间
                "hy": "0",
                "yp": "68169",
                "time": "06月23日 18:00",     //直播赛事时间
                "tit": "小小英雄【复活赛】",  //小组赛标题
                "p1": "小小英雄30进2",        //小组赛阶段
                "t1": "4399【小小英雄】",     //淘汰赛标题
                "t2": "阶段：复活赛（30进2）",//淘汰赛阶段
                "score": "0:0",               //事实比分
                "stageCn": "复活赛",
                "hf": "",
                "tid1": 1,          //队伍1 id
                "tid2": 2,          //队伍2 id
                "por2": 72.7,       //队伍2 支持率（百分比）
                "por1": 27.3,       //队伍1 支持率（百分比）
                "day": "20180623",
                "order": 119816,
                "status": 0
            },
            {
                "id": "4",
                "yxid": "4",
                "stage": "0",
                "start": "20180629 18:00",
                "end": "20180629 21:00",
                "hy": "0",
                "yp": "10585",
                "time": "06月29日 18:00",
                "tit": "小小英雄【A组决赛】",
                "p1": "小小英雄5进2",
                "t1": "4399【小小英雄】",
                "t2": "阶段：A组决赛（5进2）",
                "score": "0:0",
                "stageCn": "A组决赛",
                "hf": "",
                "tid1": 1,
                "tid2": 2,
                "por2": 52.9,
                "por1": 47.1,
                "day": "20180629",
                "order": 638216,
                "status": 0
            },
            {
                "id": "5",
                "yxid": "1",
                "stage": "0",
                "start": "20180630 14:00",
                "end": "20180630 17:00",
                "hy": "0",
                "yp": "10585",
                "time": "06月30日 14:00",
                "tit": "生死狙击【淘汰赛】",
                "p1": "生死狙击16进8",
                "t1": "4399【生死狙击】",
                "t2": "阶段：淘汰赛（16进8）",
                "score": "0:0",
                "stageCn": "淘汰赛",
                "hf": "",
                "tid1": 1,
                "tid2": 2,
                "por2": 62.2,
                "por1": 37.8,
                "day": "20180630",
                "order": 710216,
                "status": 0
            },
            {
                "id": "6",
                "yxid": "2",
                "stage": "0",
                "start": "20180630 14:00",
                "end": "20180630 17:00",
                "hy": "0",
                "yp": "10693",
                "time": "06月30日 14:00",
                "tit": "火线精英【淘汰赛】",
                "p1": "火线精英32进16",
                "t1": "4399【火线精英】",
                "t2": "阶段：淘汰赛（32进16）",
                "score": "0:0",
                "stageCn": "淘汰赛",
                "hf": "",
                "tid1": 1,
                "tid2": 2,
                "por2": 60,
                "por1": 40,
                "day": "20180630",
                "order": 710216,
                "status": 0
            }
        ],
        "yxList": [            //游戏列表
            {
                "id": "1",          //游戏id
                "key": "ssjj",      //游戏key
                "name": "生死狙击", //游戏名
                "url": "http://ssjj.4399.com",     //游戏官网链接
                "lbUrl": "http://my.4399.com/jifen/yx-ssjj",     //游戏礼包链接
                "jjbt": "生死狙击",      //游戏标题
                "wapImg": "http://f1.img4399.com/dj~2017/11/23/09_DnGSxA0vWh.239x137.jpg",
                "jjnr": "4399生死狙击是一款无插件真3D第一人称射击（FPS）网页游戏，爽快打击和华丽视效的枪战风格，打开网页，即可感受枪林弹雨的枪战乐趣。多种对战模式，实现客户端FPS游戏常规玩法无端化，让你随时随地与好兄弟战个痛快！",   //游戏内容
                "status": 0,
                "stage": "淘汰赛"
            },
            {
                "id": "2",
                "key": "hxjy",
                "name": "火线精英",
                "url": "http://news.4399.com/hxjy/",
                "lbUrl": "http://my.4399.com/jifen/yx-hxjy",
                "jjbt": "火线精英",
                "wapImg": "http://f1.img4399.com/images~2018/06/15/11_WlKK7ACFsB.362x216.png",
                "jjnr": "4399火线精英是一款时尚射击页游巨作，全3D视角，无需下载点击即玩，酷爽战斗堪比主流客户端。末世科技英雄题材，数十款劲炫武器游戏币直接购买。游戏地图风格各异，太空舰战、街头巷战一应俱全。一枪在手，天下我有！",
                "status": 0,
                "stage": "淘汰赛"
            },
            {
                "id": "3",
                "key": "xxtjd",
                "name": "小小突击队",
                "url": "http://xxtjd.4399sy.com/",
                "lbUrl": "http://xxtjd.4399sy.com/",
                "jjbt": "小小突击队",
                "wapImg": "http://f1.img4399.com/images~2018/06/15/11_NrVOBTylVp.434x302.png",
                "jjnr": "小小突击队是四三九九独立研发的一款枪战竞技手游。游戏中，小伙伴们化身为刚毅的冲锋枪战士、冷静的狙击枪手、犀利的忍者等多个英雄后，展开精彩刺激的5v5枪战，给你带来前所未有枪战的震撼！",
                "status": 0,
                "stage": "淘汰赛"
            },
            {
                "id": "4",
                "key": "xxyx",
                "name": "小小英雄",
                "url": "http://xxyx.4399sy.com/",
                "lbUrl": "http://xxyx.4399sy.com/",
                "jjbt": "小小英雄",
                "wapImg": "http://f1.img4399.com/images~2018/06/15/11_8bJzhQsULX.407x218.png",
                "jjnr": "小小英雄结合了FPS的带入感和MOBA手游的竞技感，拥有不同射击技能的英雄和各种高低地形的地图，流畅的操作和射击体验，快来加入到英雄的行列里，一起称霸枪战世界吧！",
                "status": 0,
                "stage": "复活赛"
            }
        ]
    }
}
```

### 投票

### interface  

_zt._ztUrl + "-ajaxVote"

### descrition 


### method 

POST

### param 


字段 | 类型 | 描述 |  是否必须
---|---|---|---
_AJAX_ | num | XXXX | 是
zid | num | 直播id | 是  
tid | num | 投票的队伍id | 是

### return 

```
{
    "status":1,
    "msg":"投票成功",
    "data":{
        "por1":"60",    //最新队伍1 支持率（百分比）
        "por2":"40"     //最新队伍2 支持率（百分比）
    }
}
```


