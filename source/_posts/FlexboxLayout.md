---
title: FlexboxLayout
date: 2016-05-16 22:54:10
categories: android
tags: FlexboxLayout
---


 FlexboxLayout是Android的一个功能和[CSS FLEXIBLE BOX LAYOUT](https://www.w3.org/TR/css-flexbox-1/) 类似的库。

## 使用方法

添加依赖在build.gradle中

	dependencies {
        compile 'com.google.android:flexbox:0.1.2'
	}

FlexboxLayout继承自ViewGroup，在layout XML中可以这样使用：

	<com.google.android.flexbox.FlexboxLayout
	    xmlns:android="http://schemas.android.com/apk/res/android"
	    xmlns:app="http://schemas.android.com/apk/res-auto"
	    android:layout_width="match_parent"
	    android:layout_height="match_parent"
	    app:flexWrap="wrap"
	    app:alignItems="stretch"
	    app:alignContent="stretch" >

	    <TextView
	        android:id="@+id/textview1"
	        android:layout_width="120dp"
	        android:layout_height="80dp"
	        app:layout_flexBasisPercent="50%"
	        />

	    <TextView
	        android:id="@+id/textview2"
	        android:layout_width="80dp"
	        android:layout_height="80dp"
	        app:layout_alignSelf="center"
	        />

	    <TextView
	        android:id="@+id/textview3"
	        android:layout_width="160dp"
	        android:layout_height="80dp"
	        app:layout_alignSelf="flex_end"
	        />
	</com.google.android.flexbox.FlexboxLayout>

在java代码中像下边这样使用：

		FlexboxLayout flexboxLayout = (FlexboxLayout) findViewById(R.id.flexbox_layout);
		flexboxLayout.setFlexDirection(FlexboxLayout.FLEX_DIRECTION_COLUMN);
		
		View view = flexboxLayout.getChildAt(0);
		FlexboxLayout.LayoutParams lp = (FlexboxLayout.LayoutParams) view.getLayoutParams();
		lp.order = -1;
		lp.flexGrow = 2;
		view.setLayoutParams(lp);
	

## 支持的属性

可以指定如下这些属性：

##### flexDirection

flexDirection 属性决定items在Flexbox layout中排列方向。

有四个值可以选择：

* row（默认值）：从左到右
* row-reverse：从右到左
* column：垂直方向，从上到下。
* column-reverse：垂直方向，从下到上。

效果图：
![flexDirection](http://7xu251.com1.z0.glb.clouddn.com/flex-direction.gif)

##### flexWrap

 flexWrap控制flex容器中的items是多行还是单行，该属性支持换行排列。

 有三个值

* nowrap ：不换行
* wrap：按正常方向换行
* wrap-reverse：按反方向换行

效果如图：
![flexWrap](http://7xu251.com1.z0.glb.clouddn.com/flex-wrap.gif)

##### justifyContent

这个属性控制items在主轴上的对其方式。

有五个值：

* flex_start ：(默认值)左对齐
* flex_end ：右对齐
* center ：居中
* space_between ：两端对齐，项目之间的间隔都相等。
* space_around ：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

效果图：
![justify](http://7xu251.com1.z0.glb.clouddn.com/justify-content.gif)

##### alignItems

这个属性控制竖直轴方向的对其方式。

有五个值：

* stretch (默认值) 如果项目未设置高度或设为auto，将占满整个容器的高度。
* flex_start：竖直轴的起点
* flex_end：竖直轴的终点
* center：竖直轴的中心
* baseline： 项目的第一行文字的基线对其。

效果图：
![align](http://7xu251.com1.z0.glb.clouddn.com/align-items.gif)

##### alignContent

alignContent属性定义在flex容器中多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

* stretch (默认)：轴线占满整个交叉轴。
* flex_start ：与十字轴的起点对齐
* flex_end   ：与十字轴的终点对齐
* center     ：与十字轴的中心点对其
* space_between ：与十字轴两端对齐，轴线之间的间隔平均分布。
* space_around ：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。

效果图：
![acontent](http://7xu251.com1.z0.glb.clouddn.com/align-content.gif)


英语水平有限，哪里翻译的不好或者不对，请在评论中指正！！！谢谢欣赏！！

[原文地址](https://github.com/google/flexbox-layout)





