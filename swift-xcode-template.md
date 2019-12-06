## 考虑作废
- oc.demo中对系统的模板做了较多改动
- 在做这个swift.demo时感觉没必要，就简单改了一点
- 未来会再做一版，会最小化的改动系统模板
- 但还是把过程记下来，以备忘

------

#### 定制我的swift-demo工程模板

找到源目录（系统模板所在目录）

```
cd /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/Xcode/Templates/Project\ Templates/iOS/Application
open .
```

找到目标目录（自定义模板所在目录）

```
cd ~/Library/Developer/Xcode/Templates/Project\ Templates/M2（你自定义的子目录）
// 如果没有Templates或子目录，自己创建
open .
```

把这些从源目录复制到目标目录

```
Single View App.xctemplate
Cocoa Touch App Base.xctemplate
UIScene Lifecycle.xctemplate
```

改成你想要的名字，例如

```
Single View App.xctemplate -> m2-swift-demo.xctemplate
Cocoa Touch App Base.xctemplate -> m2-swift-Cocoa Touch App Base.xctemplate
UIScene Lifecycle.xctemplate -> m2-swift-UIScene Lifecycle.xctemplate
```

改造m2-swift-Cocoa Touch App Base.xctemplate（名字以我的为例）

```
// TemplateInfo.plist
Identifier值改为xyz.chenms.swift.demo.cocoaTouchApplicationBase
各子节点中，删掉Objective-C相关项
```

改造m2-swift-UIScene Lifecycle.xctemplate

```
// TemplateInfo.plist
Identifier值改为xyz.chenms.swift.demo.sceneLifecycleApplication
Ancestors中的cocoaTouchApplicationBase项改为xyz.chenms.swift.demo.cocoaTouchApplicationBase
各子节点中，删掉Objective-C相关项
```

改造m2-swift-demo.xctemplate

```
// TemplateInfo.plist
Identifier值改为xyz.chenms.swift.demo.singleViewApplication
Ancestors清空，添加上述cocoaTouchApplicationBase和sceneLifecycleApplication
本例中为
xyz.chenms.swift.demo.cocoaTouchApplicationBase
xyz.chenms.swift.demo.sceneLifecycleApplication
各子节点中，删掉Objective-C相关项
删掉sceneDidEnterBackground:saveCoreDataContext及CoreData相关项
// Main.storyboard
将ViewController嵌入NavigationController
```

