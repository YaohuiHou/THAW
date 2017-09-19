# JsBridge

卡车之家 前端开发--native与js通信

---
##### 参考文档：[https://github.com/lzyzsd/JsBridge](https://github.com/lzyzsd/JsBridge)
---



<html>
    <h4>注: </h4>
    1. 方法名 （客户端和web端保持一致）<br/>
    2. 返回值 （统一用json格式）<br/>
    3. 有考虑不全的，及时更新文档<br/>
</html>

### 定义通用方法

1. 浏览大图

```
方法名： onShowImages
参数：  
    { 
        "current": 0,  //int类型，表示当前图片在集合中的位置，从0开始计数
        "urls":["",""]  //JSONArray类型，表示图片链接集合
    }
                   
```
2. 分享

> 分享到QQ好友


```
方法名：onShareToQQ
参数：   
    {
        title: "", // 分享标题
        desc: "", // 分享描述
        link: "", // 分享链接
        imgUrl: "" // 分享图标
        isAddCalorie: true //分享成功后是否加卡路里，true加，false不加
    }
```

> 分享到QZone


```
方法名：   onShareToQZone
参数：   
    {
        title: "", // 分享标题
        desc: "", // 分享描述
        link: "", // 分享链接
        imgUrl: "" // 分享图标
        isAddCalorie: true //分享成功后是否加卡路里，true加，false不加
    }
```

> 分享到微信好友


```
方法名：   onShareToWeChat
参数：   
    {
        title: "", // 分享标题
        desc: "", // 分享描述
        link: "", // 分享链接
        imgUrl: "" // 分享图标
        isAddCalorie: true //分享成功后是否加卡路里，true加，false不加
    }
```


> 分享到微信朋友圈


```
方法名：   onShareToTimeLine
参数：   
    {
        title: "", // 分享标题
        desc: "", // 分享描述
        link: "", // 分享链接
        imgUrl: "" // 分享图标
        isAddCalorie: true //分享成功后是否加卡路里，true加，false不加
    }

```


> 分享到新浪微博


```
方法名：   onShareToWeibo
参数：   
    {
        title: "", // 分享标题
        desc: "", // 分享描述
        link: "", // 分享链接
        imgUrl: "" // 分享图标
        isAddCalorie: true //分享成功后是否加卡路里，true加，false不加
    }
```


> 分享后，app调用web方法

```
方法名：   onShareCallback
参数：   
    {
        status:true,// 分享成功是true，失败和取消是false
        platform："" , //分享的平pengyouquan,weixin,qzone,weibo,qq,friendscircle
        msg：""  //成功或者失败信息
    }
```

> 分享到卡友圈

```
方法名： onShareToFriendsCircle
参数： 
    {
        title: "", // 分享标题
        desc: "", // 分享描述
        link: "", // 分享链接
        imgUrl: "" // 分享图标
    }
```

3.  拨打电话


```
方法名：   onDial
参数：   
    {
        tel: "01067000000", // 电话号码
    }
```




4.  打开新的web页面（例如广告，寻底价等）


```
方法名：   onOpenCommonWeb
参数：  
    {
        url: "", // 将要打开页面的url
        title: "", // 将要打开页面的title(2017.07.11)
    }
```



5.  打开文章详情页


```
方法名：   onOpenNewsWeb
参数：  
    {
        articleId: "", // 将要打开文章的id
    }
```
6.  打开帖子详情页


```
方法名：   onOpenBbsWeb
参数：  
    {
        bbsId: "", // 将要打开帖子的id
    }

// 资讯 -- 图集
    onOpenNewsPictureWeb
    
    {
    	pictureId:"23355",
    }


// 资讯 -- 视频 
    onOpenNewsVideoWeb
    
    {
    	videoId:"23355",
    }


// 卡友圈 -- 详情页 
    onOpenKYQWeb
    
    {
    	logAid:"23355"
    }

```

7.  查看个人中心


```
方法名：   onPersonCenter
参数：  
    {
        uid: "", // 个人用户论坛uid
    }
```

8.   注册登录


```
方法名：  onLogin
参数：   可以为空
```



9.  注册登录成功后，客户端调用web的方法

```

方法名： onLoginCallback
参数：   
    {
        status:true,
        data:{
            "userid":"", // 用户id
        }
    }
```



10.  Toast


```
方法名：   onToast
参数：  
    {
        message: "", 
    }
```



11.  显示Loading


```
方法名：   onShowLoading
参数：    可以为空
```



12.  隐藏Loading


```
方法名：  onHideLoading
参数：   可以为空
```
14.  显示Tabbar


```
方法名 ：   onShowTabbar
参数    ：  可以为空
```


15.  隐藏Tabbar


```
方法名 ：  onHideTabbar
参数    ：  可以为空
```


16.  隐藏返回按钮

```

方法名 ：   onHideHistoryBack
参数    ：  可以为空
```


17.   页面返回上一级


```
方法名 ：   onGoBackWeb
参数    ：   可以为空
```


18.  关闭页面


```
方法名 ：   onCloseWeb
参数    ：    可以为空
```


19.  发帖


```
方法名 ：  onPost
参数    ：   可以为空
```

20. 分享调用app原生分享页面

```

方法名 ： onShare
参数 ：  
    {
        title: "", // 分享标题
        desc: "", // 分享描述
        link: "", // 分享链接
        imgUrl: "" // 分享图标
        isAddCalorie: true //分享成功后是否加卡路里，true加，false不加
    }
```


21. 上传图片

> A

```
方法名 ：   onImageUpload（旧版本app中使用）
参数：      
    {
        uploadUrl: "", 上传接口
    }

// 改成客户端上传到七牛后

方法名 ：   onImageUpload（新版本6.1.0以后）
参数：  
    {
        bucket："" 图片上传到七牛的桶名，比如bbsimage
        imgPath："" 图片上传文件路径 比如 imga/nr/t/
        hostUrl："" 图片上传域名 比如 https://img9.kcimg.cn/
    }
```

 
> B 上传成功后回调给web端

```
方法名 ：   onImageUploadCallBack(app->js,2017.06.22)
参数：      
    {
        "status": "1",//1表示成功
        "linkUrl": "https://img6.kcimg.cn/bbs/month_1706/b9835b9f49c442378281f0fbb853566c.jpg",//图片原地址
        "imgUrl": "b9835b9f49c442378281f0fbb853566c.jpg|0|0",//求助使用
        "msg": "图片上传成功"
    }
```
22. 删除举报对话框（帖子详情页）


```
方法名 ： onShowDeleteDialog
参数：   
    {
        type: "", // type=1，删除   type=2 举报
        pid: "", //
        action:"pull"
    }
```


23.  点击删除确定按钮（帖子详情页）


```
方法名 ： onDeleteConfirm
参数：   
    {
        type: "", // type=1，删除   type=2 举报
        pid: "", //
        action:"pull"
    }
```



24. 删除帖子成功后，web会调用客户端的方法退出web页面


```
方法名： back2list
参数  ： 可以为空
```


25.  web也是否需要可变title


```
方法名： onAutoChangeWebTitle
参数： 
    {
        autoChangeWebTitle: true, // 值是boolean ，true表示客户端为跳转各页设置title
    }
```

26.  web设置title


```
方法名： onChangeWebTitle 
参数： 
    {
        changeWebTitle: “标题”, // title
    }
```


27.  帖子详情页 ，主帖删除成功后回调

```
方法名： onShowDeleteDialog
参数  ： 为空
```


28  帖子详情页 ，回帖删除成功后回调

```
方法名： onDeleteCommentSuccess
参数： 
    {
        status:"1"   1表示成功，0表示失败
    }
```


29.  手机震动

```
方法名： onVibrate
参数  ：为空
```


30.  查看个人信息

```
方法名： memberinfo
参数：
    {
        "uid":"" //论坛uid
    }
```


31. 签到中身份认证

```
方法名 ：   onPersonAuthentication（js->app 2017.06.20）
参数：  
    {
        "type":1 // int 类型 0 调用系统的相机1表示身份证正面, 2表示身份证反面, 3表示正脸照片, 4表示驾驶证, 5表示行驶证, 6表示车牌照
        “bucket”：“”    // 图片上传到七牛的桶名，比如bbsimage
        “imgPath”：“”  // 图片上传文件路径 比如 imga/nr/t/
        “hostUrl”：“”    //图片上传域名 比如 https://img9.kcimg.cn/
    }
```
