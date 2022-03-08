# QA:

## TUICalling：

### Q:  TUICalling场景有没有悬浮框设计？

**A:** 预计9.6版本会发出悬浮窗版本。

### Q:  能不能不引入IM SDK，只使用TRTC, 可以吗？

**A:**  场景化需要IM做为通信的基础服务，IM的基础功能是免费的，目前TRTC和IM是无法独立分开使用后期可以根据需求选择是否升级。

## TUIRoom：

### Q:  iOS集成Demo报错，缺少文件？

**A:**  XLiteAVSDK_ReplayKitExt framework集成错误，https://github.com/tencentyun/TRTCSDK/tree/master/iOS/SDK 参考里面的framework。

## 小直播：

### Q:  iOS直播录屏发起推流后，返回了“集成错误（SDK版本号不相符合）” ？

**A:**  ReplayKitEx，Live 这个两个framework版本号不一致导致的问题，需要下载相同的版本。