# PhotoEditor
本demo为基本图片编辑，可对照片进行椭圆、矩形、文字涂鸦绘制，并有extensions，可在照片应用调用。
其实是有3个版本，第一个版本卡顿现象严重，采用双层view设计，上层view是绘图层（背景透明），只绘制当前画的图形，当手指离开屏幕，
将上层图形绘制到背景层，因为背景层很大，每次移动手指都要操作很大的区域，第二个版本绘制大图片还是有些卡顿，跟第一版本结构类似，
采用3层view结构，当手指离开屏幕，不直接在背景层绘制，而是在中间层绘制，最后要使用的时候再绘制到背景层，前面两个版本都会出现
编辑多次模糊问题，最后这个版本修正了这个问题，采用多层view结构，只有顶层view响应触摸事件，每次绘制区域都只有绘制图形的大小，
不需要绘制展示图像区域那么大，保存的时候才绘制背景层。也就是说用户绘图的时候并不是直接在照片上绘制，而是在比原照片小的多的透
明视图上绘制，保证ui的响应和用户的体验。
另外，撤销功能的基本思想就是把最进添加的view remove掉。