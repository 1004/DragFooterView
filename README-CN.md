# DragFooterView

![](https://jitpack.io/v/uin3566/DragFooterView.svg)    
一个向左拖拽跳转至更多页面的通用控件    

## Demo
![screenshot](/screenshot/demo.gif)
 
 
## 灵感来源
 下面是原作的效果，在一个App上看到的，于是就自己实现了一下，
 并封装成了一个通用的控件，这个控件既涉及到了自定义View的绘制， 
 也涉及到了View的事件分发，正好借机巩固了一把这些知识，
 功力又深了一层，哈^_^。
![screenshot](/screenshot/inspiration.gif)  

## 自定义你自己的Footer效果   
作为一个library，当然不能只支持以上那一种效果啦，所以，这个库的
Footer应该是可定制的，可插拔的。定制Footer只需定义一个继承自
BaseFooterDrawer的类，然后在参数中提供的区域中绘制即可，而其余
的事件分发，拦截都不需要关心。以下是我自己定制的两种Footer效果。    
![screenshot](/screenshot/custom1.gif)    
![screenshot](/screenshot/custom2.gif) 

## 添加依赖
* step1:Add it in your root build.gradle at the end of repositories:
```xml
    allprojects {
        repositories {
            ...
	        maven { url "https://jitpack.io" }
        }
    }
```
* step2:Add the dependency:
```
    dependencies {
        compile 'com.github.uin3566:DragFooterView:v1.0.1'
    }
```

## 用法
1、在xml中配置如下 **(注意：DragContainer只能有一个子View)**
```xml
    <com.fangxu.library.DragContainer
        android:id="@+id/drag_recycler_view"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="10dp">

        <android.support.v7.widget.RecyclerView
            android:id="@+id/recycler_view"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="@android:color/white" />
    </com.fangxu.library.DragContainer>
```
2、在java类中添加事件监听器DragListener
```java
    DragContainer dragContainer = (DragContainer) findViewById(R.id.drag_image_view);
    
    //若需使用自己定制的footer，需要调用DragContainer的setFooterDrawer方法设置定制的footer类，如下
    dragContainer.setFooterDrawer(new ArrowPathFooterDrawer.Builder(this, 0xff444444).setPathColor(0xffffffff).build());
    
    dragContainer.setDragListener(new DragListener() {
        @Override
        public void onDragEvent() {
            //do whatever you want,for example skip to the load more Activity.
            Intent intent = new Intent(HomeActivity.this, ShowMoreActivity.class);
            startActivity(intent);
        }
    });
```

## 属性
|attribute|value type|defalut value| description|
| --- | --- | --- | --- |
|dc_footer_color|color|0xffcdcdcd|footer view的背景颜色|
|dc_reset_animator_duration|integer|700|松开拖拽后复位动画的时长|
|dc_drag_damp|float|0.5f|拖拽阻尼系数，取值在(0,1]之间，取值越小，阻尼越大|


## License
```
Copyright (c) 2016 uin3566 <xufang2@foxmail.com>

Licensed under the Apache License, Version 2.0 (the "License”);
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
   
   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
