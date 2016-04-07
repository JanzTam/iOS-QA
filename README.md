# iOS-QA
 A collection of Frequently Asked Questions for iOS.

# 为什么要创建这个库？
为了让大家的知识可以互相吸收、学习、借鉴xxxx。。以后大家提问题尽量说得明白一点啊，对自己也好，对别人也好。我们这里小白问题也可以问，但是记得态度要诚恳啊。以后就别开口就大神什么的了。可以这样说：我遇到一个问题，然后说问题的内容，然后说大家觉得应该怎么解决的blabla。最后可以将问题，和最终的解决方案发给我，我整理传上Github去，以后重复问题就直接在那里找了。而解决完的Demo你们自己在Github上创个库，然后甩链接给我就行了。

# QA
第0个：Example：

Q:我遇到一个问题，我在UITableView里加了很多圆角，滑动的时候很卡，请问大家有什么好的解决方案吗？

A:某成员：你可以在加载图片的时候用CAShapeLayer先给这个图片加个遮罩，然后用SDWebImage来做缓存。Demo地址：https://github.com

***

1、From @嗷大喵

Q:如何实现映客那种点赞动画？

A:DMHeartFlyAnimation https://github.com/singer1026/DMHeartFlyAnimation


2、From @匿名

Q:为什么touchesBegan不响应？我想在一个UIScrollView上通过touchesBegan关闭键盘，但是无法响应。
```Objc
- (void)touchesBegan:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event {
    [self.view endEditing:YES];
}
```

A:通过UIScrollView类目，重写touches方法
```Objc
@implementation UIScrollView (UITouchEvent)

- (void)touchesBegan:(NSSet *)touches withEvent:(UIEvent *)event {
    [[self nextResponder] touchesBegan:touches withEvent:event];
    [super touchesBegan:touches withEvent:event];
}
-(void)touchesMoved:(NSSet *)touches withEvent:(UIEvent *)event {
    [[self nextResponder] touchesMoved:touches withEvent:event];
    [super touchesMoved:touches withEvent:event];
}

- (void)touchesEnded:(NSSet *)touches withEvent:(UIEvent *)event {
    [[self nextResponder] touchesEnded:touches withEvent:event];
    [super touchesEnded:touches withEvent:event];
}

@end
```

