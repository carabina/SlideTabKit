# SlideTabKit

![](https://img.shields.io/badge/language-swift-orange.svg) ![](https://img.shields.io/cocoapods/l/SlideTabKit.svg?style=flat) ![](https://img.shields.io/cocoapods/v/SlideTabKit.svg?style=flat) [![](https://img.shields.io/badge/weibo-@小鱼周凌宇-red.svg)](http://weibo.com/coderfish)

![](SlideTabKit.png)

# Introduction 

> [中文介绍](README_ZH.md)

![](res/SlideTabKit-04.png)

SlideTabKit is a simple and easy to use tools of slide tab.

"Slide Tab Tool" and "Paging tool" can be used in combination or split.

# Install

```
pod 'SlideTabKit'
```

# Example

## Use the SlideTabKit

![](res/SlideTabKit-01.gif)

```swift
var slideTabKit: SlideTabKit = SlideTabKit()
var vcs: [UIViewController] = []
var titles: [String] = ["Tab 0", "Tab 1", "Tab 2", "Tab 3"]

override func viewDidLoad() {
    super.viewDidLoad()

    for _ in 0 ..< 4 {
        let vc = UIViewController()
        vc.view.backgroundColor = UIColor.randomColor
        vcs.append(vc)
    }
    view.addSubview(slideTabKit.slideTabBar)
    slideTabKit.slideTabBar.snp.makeConstraints { (make) in
        make.top.equalTo(topLayoutGuide.snp.bottom)
        make.left.right.equalTo(view)
        make.height.equalTo(40)
    }
    slideTabKit.slideTabBar.resetting(titles: titles)

    view.addSubview(slideTabKit.slideScrollView)
    slideTabKit.slideScrollView.snp.makeConstraints { (make) in
        make.top.equalTo(slideTabKit.slideTabBar.snp.bottom)
        make.left.right.bottom.equalTo(view)
    }
    slideTabKit.slideScrollView.resetting(childViews: vcs.map({ (vc) -> UIView in
        return vc.view
    }))
}
```

## Use SlideTabBar alone

![](res/SlideTabKit-03.gif)

```swift

var slideTabBar0: SlideTabBar = SlideTabBar()

override func viewDidLoad() {
    super.viewDidLoad()

    // 设置 slideTabBar
    self.view.addSubview(slideTabBar0)
    // 其他属性设置完毕后调用 resetting
    slideTabBar0.resetting(titles: ["Tab 1", "Tab 2", "Tab 3", "Tab 4"])
    slideTabBar0.delegate = self

    slideTabBar0.snp.makeConstraints { (make) in
        make.top.equalTo(self.topLayoutGuide.snp.bottom)
        make.left.right.equalTo(self.view)
        make.height.equalTo(40)
    }
}
```

In addition to using text to initialize the style, also support custom style.

## Use SlideScrollView alone

![](res/SlideTabKit-02.gif)

```swift
var vcs: [UIViewController] = []

override func viewDidLoad() {
    super.viewDidLoad()

    for _ in 0 ..< 4 {
        let vc = UIViewController()
        addChildViewController(vc)
        vcs.append(vc)
        
        vc.view.backgroundColor = UIColor.randomColor
    }

    self.view.addSubview(slideScrollView)
    let views = vcs.map { (viewController) -> UIView in
        return viewController.view
    }
    slideScrollView.resetting(childViews: views)
    slideScrollView.delegate = self
    slideScrollView.snp.remakeConstraints { (make) in
        make.edges.equalTo(self.view)
    }
}
```

# Demo

It is recommended to download the [Demo](Demo) to see how to use SlideTabKit.

# Feature

- [x] "Slide Tab Tool" and "Paging tool" used in combination
- [x] Use SlideTabBar alone
- [x] Use paging tool alone
- [ ] The text on the tab bar fades


# License

SlideTabKit use [GNU GENERAL PUBLIC LICENSE Version 3](LICENSE)

# Feedback

If there are any suggestions, pleas send an email to <coderfish@163.com>, and also welcome to my [blog](http://zhoulingyu.com) to discuss. Learning together~



