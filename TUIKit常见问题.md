# QA:

## TUICalling：

### Q:  场景中有没有悬浮框设计？

**A:**  预计9.6版本会发出悬浮窗版本。

### Q:  能不能不引入IM SDK，只使用TRTC, 可以吗？

**A:**  场景化需要IM做为通信的基础服务，IM的基础功能是免费的，目前TRTC和IM是无法独立分开使用后期可以根据需求选择是否升级。

### Q:  iOS组件中如何监听谁在说话？ 

**A:**  可以通过下面方法来判断 volume: 说话者的音量, 取值范围0 - 100
        -(void)onUserVoiceVolume:(NSString *)uid volume:(UInt32)volume
        NS_SWIFT_NAME(onUserVoiceVolume(uid:volume:));
        
### Q:  iOS怎么实现一对多呼叫？

**A:**  可以在呼叫方法传多个用户id： - (void)call:(NSArray<NSString *> *)userIDs type:(TUICallingType)type NS_SWIFT_NAME(call(userIDs:type:));
        
### Q：必须要在应用内才能收到通话请求吗?

**A：** 应用外也可以收到请求。TUICalling已支持离线推送，源码地址：https://github.com/tencentyun/TUICalling

离线推送接入请查看：

[Android离线接入指引](https://github.com/tencentyun/TUICalling/blob/main/Android/Android%E7%A6%BB%E7%BA%BF%E6%8E%A8%E9%80%81%E6%8E%A5%E5%85%A5%E6%8C%87%E5%BC%95.md)

[iOS离线接入指引](https://github.com/tencentyun/TUICalling/blob/main/iOS/iOS%20%E7%A6%BB%E7%BA%BF%E6%8E%A8%E9%80%81%E6%8E%A5%E5%85%A5%E6%8C%87%E5%BC%95.md)

### Q：无法拨打电话
**A：** 1. 查看是否进入TRTC房间失败;
   
   可以监听 `onEnterRoom`，返回值result小于0，说明进房失败；大于0，进房成功。

2. 检查请求信令是否发送成功，在log中搜索
   ```
   //失败
   invite failed 
   //成功
   invite success
   ```        

****  
        
## TUIRoom：

### Q:  iOS集成Demo报错，缺少文件？

**A:**  XLiteAVSDK_ReplayKitExt framework集成错误，https://github.com/tencentyun/TRTCSDK/tree/master/iOS/SDK 参考里面的framework。

### Q: Windows 项目能把视频画面放在主画面上？

**A:**  计划9.6版本支持

### Q: TUIRoom 如何在用户进入房间的获取用户名（onUserEnterRoom  回调参数 只有 userId）？

**A:**  可以通过TUIRoomUserManage的方法：+ (nullable TUIRoomUserInfo *)getUser:(NSString *)userId; 获取用户信息


****


## 小直播：

### Q:  iOS直播录屏发起推流后，返回了“集成错误（SDK版本号不相符合）” ？

**A:**  ReplayKitEx，Live 这个两个framework版本号不一致导致的问题，需要下载相同的版本。

### Q:  跑通小直播 demo，一定要搭建后台服务吗？

**A:**  目前是需要后台服务的，我们正在着手将后台服务变成可选，预计2022\04\01发布~

## TUILiveRoom：

### Q:  实时音视频性能数据怎样？

**A:**  可以参考链接：https://cloud.tencent.com/document/product/647/56382#.E5.8F.82.E6.95.B0.E9.85.8D.E7.BD.AE。

        
### Q:  iOS版本demo下载后编译报错？
```
TUILiveRoom/TRTC (from `./`) was resolved to 1.0.0, which depends on
      TXIMSDK_Plus_iOS (~> 5.7.1435)
```

问题原因： Podfile.lock IMSDK版本库依赖不一致导致pod install失败

处理建议： 需要更新Pofile.lock 文件 或者 直接Gtihub仓库删除 Podfile.lock

快速处理：执行命令 `pod install --repo-update`
    
****

## TUIVoiceRoom：

### Q:  语音聊天室有Flutter Demo吗？ 

**A：**  语音聊天室暂时没有Flutter版本，如果有需要，可以点击这里登记一下：[腾讯云需求收集表](https://docs.qq.com/form/page/DZlhYYWNCaFpmaVNl?from_page=doc_list_new_form&templateId=6z9bq8gcmprmpyapp7asqjobfo&create_type=2#/fill)

我们会定期进行评估。

****


## 其他

### 怎么知道签名有效时间，是否可以修改?
**A：** 账号问题请查看官网文档：[账号鉴权相关问题](https://cloud.tencent.com/document/product/269/32484#.E5.A6.82.E4.BD.95.E7.94.9F.E6.88.90-usersig.EF.BC.9F)
