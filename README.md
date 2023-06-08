> 此项目已经归档，如果需要使用 App 检查更新功能请移步至 [PGYER/AppUpdateChecker](https://github.com/PGYER/AppUpdateChecker)

# AppVersionCheckAndroid

本项目演示了如何使用 PGYER 蒲公英的 API 在 Android App 中检查版本是否有更新

### 使用方式

首先拷贝本项目中的 com.pgyer.pgyerappupdater.pgyerutils 文件夹中的的三个文件到您的 Android 项目中，然后在需要获取更新版本的位置，调用类中提供的方法方法 `PgyUpdateVersion.checkVersionUpdate()` 方法，示例如下：

```java
PgyUpdateVersion.checkVersionUpdate("<YOUR-PGYER_API_KEY>","<YOUR-PGYER_APP_KEY>","","<APP-VERSION-NAME>",new PgyCheckoutCallBack() {
  @Override
  public void onNewVersionExist(PgyCheckSoftModel model) {
    // 检测到新版本，可根据 JsonUtils.toJSONString(model) 获取到版本信息
  }

  @Override
  public void onNonentityVersionExist(String error) {
    // 没有新版本
  }

  @Override
  public void onFail(String error) {
    // 请求失败
  }
});
```

如果存在新版本，那么在 `onNewVersionExist` 中可以获取到新版本中的信息。在 `PgyCheckSoftModel` 中已备注具体字段说明
