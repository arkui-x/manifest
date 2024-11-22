# 获取源码

简体中文 | [English](README-EN.md)

## ArkUI-X项目

ArkUI-X项目进一步将ArkUI开发框架扩展到了多个OS平台：目前支持OpenHarmony、HarmonyOS、Android、 iOS，后续会逐步增加更多平台支持。开发者基于一套主代码，就可以构建支持多平台的精美、高性能应用。

开源代码仓库地址：[https://gitee.com/arkui-x](https://gitee.com/arkui-x)。

## 前提条件

1. 注册码云gitee账号。

2. 注册码云SSH公钥，请参考[码云帮助中心](https://gitee.com/help/articles/4191)。

3. 安装[git客户端](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)和[git-lfs](https://gitee.com/vcs-all-in-one/git-lfs?_from=gitee_search#downloading)并配置用户信息。

   ```
   git config --global user.name "yourname"
   git config --global user.email "your-email-address"
   git config --global credential.helper store
   ```

4. 安装码云repo工具，可以执行如下命令。

   ```
   curl -s https://gitee.com/oschina/repo/raw/fork_flow/repo-py3 > /usr/local/bin/repo  #如果没有权限，可下载至其他目录，并将其配置到环境变量中
   chmod a+x /usr/local/bin/repo
   pip3 install -i https://repo.huaweicloud.com/repository/pypi/simple requests
   ```

## 操作步骤

- **ArkUI-X主干代码获取**

  方式一（推荐）：通过repo + ssh下载（需注册公钥，请参考[码云帮助中心](https://gitee.com/help/articles/4191)）。

  ```
  mkdir arkui
  cd arkui
  repo init -u git@gitee.com:arkui-x/manifest.git -b master --no-repo-verify
  repo sync -c --no-tags -j12
  ```

  方式二：通过repo + https下载。

  ```
  mkdir arkui
  cd arkui
  repo init -u https://gitee.com/arkui-x/manifest.git -b master --no-repo-verify
  repo sync -c
  repo forall -c 'git lfs pull'
  ```

- **ArkUI-X开发分支代码获取**

  方式一（推荐）：通过repo + ssh下载（需注册公钥，请参考[码云帮助中心](https://gitee.com/help/articles/4191)）。

  ```
  mkdir arkui
  cd arkui
  repo init -u git@gitee.com:arkui-x/manifest.git -b master --no-repo-verify -m arkui-dev.xml
  repo sync -c --no-tags -j12
  ```

  方式二：通过repo + https下载。

  ```
  mkdir arkui
  cd arkui
  repo init -u https://gitee.com/arkui-x/manifest.git -b master --no-repo-verify -m arkui-dev.xml
  repo sync -c --no-tags -j12
  ```

# 代码工程介绍

## 代码结构及仓库结构

代码工程的目录结构如下：
```
├── arkcompiler                 // 方舟编译器
├── base                        // 基础能力
├── build                       // 项目构建和配置脚本
├── build_plugins               // 跨平台构建插件
├── commonlibrary               // 公共基础库
├── community                   // 社区相关
├── developtools                // 开发者工具
├── docs                        // 配套文档
├── foundation
│   ├── appframework            // 应用框架兼容适配层
│   ├── arkui                   // ArkUI引擎
│   ├── communication           // 通信能力
│   ├── distributeddatamgr      // 分布式数据管理
│   ├── filemanagement          // 文件管理
│   ├── graphic                 // 图形引擎
│   └── multimedia              // 多媒体
├── interface                   // 接口声明
├── plugins                     // 插件管理与实现
├── prebuilts                   // 预编译目录
├── productdefine               // 产品形态配置
├── samples                     // 示例代码
├── test                        // 测试框架与测试套件用例
└── third_party                 // 三方库
```

具体的代码结构及仓指向，见下表：

| 目录路径                                  | 描述                                                  | 代码仓位置                                                   |
| ----------------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------ |
| build                                     | 项目构建和配置脚本                         | [OpenHarmony/build](https://gitee.com/openharmony/build) |
| build_plugins                             | 跨平台构建插件                        | [ArkUI-X/build_plugins](https://gitee.com/arkui-x/build_plugins) |
| samples                                   | 应用程序样例                                          | [ArkUI-X/samples](https://gitee.com/arkui-x/samples) |
| community                                 | 社区运作管理                                          | [ArkUI-X/community](https://gitee.com/arkui-x/community) |
| docs                                      | 说明文档                                              | [ArkUI-X/docs](https://gitee.com/arkui-x/docs) |
| developtools/ace_tools                    | 跨平台应用构建命令行工具                                      | [ArkUI-X/cli](https://gitee.com/arkui-x/cli) |
| foundation/appframework | 应用框架兼容适配层    | [ArkUI-X/app_framework](https://gitee.com/arkui-x/app_framework) |
| foundation/arkui/ace_engine/adapter/android | Android平台适配代码                                   | [ArkUI-X/arkui_for_android](https://gitee.com/arkui-x/arkui_for_android) |
| foundation/arkui/ace_engine/adapter/ios     | iOS平台适配代码                                       | [ArkUI-X/arkui_for_ios](https://gitee.com/arkui-x/arkui_for_ios) |
| foundation/arkui/ace_engine                 | ArkUI引擎核心代码 | [OpenHarmony/arkui_ace_engine](https://gitee.com/openharmony/arkui_ace_engine) |
| foundation/arkui/napi                       | Native API扩展机制                                    | [OpenHarmony/arkui_napi](https://gitee.com/openharmony/arkui_napi) |
| foundation/graphic/graphic_2d               | 2D图形基础库                                    | [OpenHarmony/graphic_graphic_2d](https://gitee.com/openharmony/graphic_graphic_2d) |
| arkcompiler/ets_frontend                          | 方舟前端工具                        | [OpenHarmony/arkcompiler_ets_frontend](https://gitee.com/openharmony/arkcompiler_ets_frontend) |
| arkcompiler/ets_runtime                          | 方舟ArkTS运行时                        | [OpenHarmony/arkcompiler_ets_runtime](https://gitee.com/openharmony/arkcompiler_ets_runtime) |
| arkcompiler/runtime_core                          | 方舟编译器运行时                        | [OpenHarmony/arkcompiler_runtime_core](https://gitee.com/openharmony/arkcompiler_runtime_core) |
| arkcompiler/toolchain                          | 调试调优工具                        | [OpenHarmony/arkcompiler_toolchain](https://gitee.com/openharmony/arkcompiler_toolchain) |
| prebuilts                                 | 预编译目录，python，nodejs，clang和cmake等            | 通过脚本预下载                                               |
| third_party                               | 开源第三方组件（统一复用OpenHarmony代码仓）           | 引用开源三方库集合 |
| commonlibrary/c_utils                              | C++公共基础类库                                          | [OpenHarmony/commonlibrary_c_utils](https://gitee.com/openharmony/commonlibrary_c_utils) |
| base/global/resource_management                          | 全球化资源管理                                          | [OpenHarmony/global_resource_management](https://gitee.com/openharmony/global_resource_management) |
| plugins                              | API插件管理，OpenHarmony API插件实现                                  | [ArkUI-X/plugins](https://gitee.com/arkui-x/plugins) |
| test/xts               | ArkUI-X应用测试套件      | [ArkUI-X/xts](https://gitee.com/arkui-x/xts) |
| test/testfwk/arkxtest                | ArkUI-X测试框架       | [ArkUI-X/arkxtest](https://gitee.com/arkui-x/arkxtest) |
| interface/sdk                | ArkUI-X SDK相关配置       | [ArkUI-X/interface_sdk](https://gitee.com/arkui-x/arkxtest) |
| productdefine/common               | ArkUI-X产品形态定义       | [ArkUI-X/productdefine](https://gitee.com/arkui-x/productdefine) |

> 说明：OpenHarmony相关代码仓，指向OpenHarmony master分支的固定tag点，定期同步，默认按照OpenHarmony的Weekly分支频率进行同步。

## ArkUI引擎核心代码仓目录结构

ArkUI引擎核心代码仓 `ace_engine` 的目录结构以及每个目录的内容如下：

```
foundation/arkui/ace_engine
├── ace_config.gni      // 全局配置文件
├── adapter             // 平台适配层
│   ├── android         // Android平台适配，独立仓
│   │   ├── build
│   │   ├── capability
│   │   ├── entrance
│   │   ├── stage
│   │   └── osal
│   ├── ios             // iOS平台适配，独立仓
│   │   ├── build
│   │   ├── capability
│   │   ├── entrance
│   │   ├── stage
│   │   └── osal
│   ├── ohos            // OpenHarmony平台适配
│   └── preview         // 预览器平台适配
├── build               // 编译配置
│   ├── ace_gen_obj.gni
│   ├── ace_lib.gni
│   ├── BUILD.gn
│   ├── search.py
│   └── tools
├── BUILD.gn            // 全局编译配置
├── frameworks          // 引擎框架层
│   ├── base            // base库
│   ├── bridge          // 前端桥接
│   └── core            // 引擎核心实现
├── interfaces          // 通用对外接口
│   └── napi
│       └── kits
├── LICENSE
├── OAT.xml
├── README.md
├── README_zh.md
└── test                // 测试相关
```
