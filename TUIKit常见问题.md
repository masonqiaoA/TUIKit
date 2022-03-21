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
        
        
        
        
## TUIRoom：

### Q:  iOS集成Demo报错，缺少文件？

**A:**  XLiteAVSDK_ReplayKitExt framework集成错误，https://github.com/tencentyun/TRTCSDK/tree/master/iOS/SDK 参考里面的framework。

### Q: Windows 项目能把视频画面放在主画面上？

**A:**  计划9.6版本支持

### Q: TUIRoom 如何在用户进入房间的获取用户名（onUserEnterRoom  回调参数 只有 userId）？

**A:**  可以通过TUIRoomUserManage的方法：+ (nullable TUIRoomUserInfo *)getUser:(NSString *)userId; 获取用户信息





## 小直播：

### Q:  iOS直播录屏发起推流后，返回了“集成错误（SDK版本号不相符合）” ？

**A:**  ReplayKitEx，Live 这个两个framework版本号不一致导致的问题，需要下载相同的版本。

### Q:  跑通小直播 demo，一定要搭建后台服务吗？

**A:**  目前是需要后台服务的，我们正在着手将后台服务变成可选，预计2022\04\01发布~

## TUILiveRoom：

### Q:  实时音视频性能数据怎样？

**A:**  可以参考链接：https://cloud.tencent.com/document/product/647/56382#.E5.8F.82.E6.95.B0.E9.85.8D.E7.BD.AE。



