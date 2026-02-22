## Clash Meta for Android

A Graphical user interface of [Clash.Meta](https://github.com/MetaCubeX/Clash.Meta) for Android

### Feature

Feature of [Clash.Meta](https://github.com/MetaCubeX/Clash.Meta)

[<img src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png"
     alt="Get it on F-Droid"
     height="80">](https://f-droid.org/packages/com.github.metacubex.clash.meta/)

### Requirement

- Android 5.0+ (minimum)
- Android 7.0+ (recommend)
- `armeabi-v7a` , `arm64-v8a`, `x86` or `x86_64` Architecture

### Build

1. Update submodules

   ```bash
   git submodule update --init --recursive
   ```

2. Install **OpenJDK 11**, **Android SDK**, **CMake** and **Golang**

3. Create `local.properties` in project root with

   ```properties
   sdk.dir=/path/to/android-sdk
   ```

4. (Optional) Custom app package name. Add the following configuration to `local.properties`.

   ```properties
   # config your ownn applicationId, or it will be 'com.github.metacubex.clash'
   custom.application.id=com.my.compile.clash
   # remove application id suffix, or the applicaion id will be 'com.github.metacubex.clash.alpha'
   remove.suffix=true

5. Create `signing.properties` in project root with

   ```properties
   keystore.path=/path/to/keystore/file
   keystore.password=<key store password>
   key.alias=<key alias>
   key.password=<key password>
   ```

6. Build

   ```bash
   ./gradlew app:assembleAlphaRelease
   ```

### Automation

APP package name is `com.github.metacubex.clash.meta`

- Toggle Clash.Meta service status
  - Send intent to activity `com.github.kr328.clash.ExternalControlActivity` with action `com.github.metacubex.clash.meta.action.TOGGLE_CLASH`
- Start Clash.Meta service
  - Send intent to activity `com.github.kr328.clash.ExternalControlActivity` with action `com.github.metacubex.clash.meta.action.START_CLASH`
- Stop Clash.Meta service
  - Send intent to activity `com.github.kr328.clash.ExternalControlActivity` with action `com.github.metacubex.clash.meta.action.STOP_CLASH`
- Import a profile
  - URL Scheme `clash://install-config?url=<encoded URI>` or `clashmeta://install-config?url=<encoded URI>`

### Contribution and Project Maintenance

#### Meta Kernel

- CMFA uses the kernel from `android-real` branch under `MetaCubeX/Clash.Meta`, which is a merge of the main `Alpha` branch and `android-open`.
  - If you want to contribute to the kernel, make PRs to `Alpha` branch of the Meta kernel repository.
  - If you want to contribute Android-specific patches to the kernel, make PRs to  `android-open` branch of the Meta kernel repository.

#### Maintenance

- When `MetaCubeX/Clash.Meta` kernel is updated to a new version, the `Update Dependencies` actions in this repo will be triggered automatically.
  - It will pull the new version of the meta kernel, update all the golang dependencies, and create a PR without manual intervention.
  - If there is any compile error in PR, you need to fix it before merging. Alternatively, you may merge the PR directly.
- Manually triggering `Build Pre-Release` actions will compile and publish a `PreRelease` version.
- Manually triggering `Build Release` actions will compile, tag and publish a `Release` version.
  - You must fill the blank `Release Tag` with the tag you want to release in the format of `v1.2.3`.
  - `versionName` and `versionCode` in `build.gradle.kts` will be automatically bumped to the tag you filled above.

add
Clash Meta for Android
 
Clash.Meta 内核的 Android 图形化客户端
 
 
 
核心功能
 
所有核心功能均继承自 Clash.Meta 内核
 
前往 F-Droid 下载
 
 
 
运行要求
 
- 最低支持 Android 5.0 及以上系统
- 推荐使用 Android 7.0 及以上系统
- 支持  armeabi-v7a 、 arm64-v8a 、 x86 、 x86_64  处理器架构
 
 
 
编译指南
 
1. 更新子模块
bash  
git submodule update --init --recursive
 
2. 安装依赖环境：OpenJDK 11、Android SDK、CMake 与 Golang
3. 在项目根目录创建  local.properties  文件，添加如下配置
properties  
sdk.dir=你的 Android SDK 存放路径
 
4. （可选）自定义应用包名，在  local.properties  中追加如下配置
properties  
# 配置自定义的应用ID，不配置则默认为 com.github.metacubex.clash
custom.application.id=com.my.compile.clash
# 移除应用ID后缀，不配置则应用ID会自动追加 .alpha 后缀
remove.suffix=true
 
5. 在项目根目录创建  signing.properties  签名配置文件
properties  
keystore.path=你的密钥库文件路径
keystore.password=密钥库密码
key.alias=密钥别名
key.password=密钥密码
 
6. 执行编译
bash  
./gradlew app:assembleAlphaRelease
 
 
 
 
自动化控制
 
应用包名： com.github.metacubex.clash.meta 
 
- 切换 Clash.Meta 服务启停状态
向活动  com.github.kr328.clash.ExternalControlActivity  发送动作值为  com.github.metacubex.clash.meta.action.TOGGLE_CLASH  的意图（Intent）
- 启动 Clash.Meta 服务
向活动  com.github.kr328.clash.ExternalControlActivity  发送动作值为  com.github.metacubex.clash.meta.action.START_CLASH  的意图（Intent）
- 停止 Clash.Meta 服务
向活动  com.github.kr328.clash.ExternalControlActivity  发送动作值为  com.github.metacubex.clash.meta.action.STOP_CLASH  的意图（Intent）
- 导入配置文件
调用 URL Scheme： clash://install-config?url=<编码后的URI>  或  clashmeta://install-config?url=<编码后的URI> 
 
 
 
贡献指南与项目维护
 
Meta 内核
 
本客户端使用的内核来自  MetaCubeX/Clash.Meta  仓库的  android-real  分支，该分支由主开发分支  Alpha  与 Android 专属分支  android-open  合并而成。
 
- 若你想为内核通用功能贡献代码，请向 Meta 内核仓库的  Alpha  分支提交合并请求（PR）
- 若你想为内核提交 Android 平台专属的补丁，请向 Meta 内核仓库的  android-open  分支提交合并请求（PR）
 
维护规则
 
- 当  MetaCubeX/Clash.Meta  内核发布新版本时，本仓库的  Update Dependencies  工作流会自动触发
- 自动拉取新版本内核、更新所有 Golang 依赖并创建合并请求，全程无需人工干预
- 若自动生成的合并请求出现编译错误，需修复问题后再合并，也可选择直接合并
- 手动触发  Build Pre-Release  工作流，会自动编译并发布一个预发布版本
- 手动触发  Build Release  工作流，会自动完成编译、打标签并发布正式版本
- 必须在  Release Tag  输入框中填写符合  v1.2.3  格式的发布标签
-  build.gradle.kts  中的  versionName （版本名）与  versionCode （版本号）会根据填写的标签自动同步更新
