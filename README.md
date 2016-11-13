# DragFooterView

![](https://jitpack.io/v/uin3566/DragFooterView.svg)  
A ViewGroup with a draggable footer

![screenshot](/screenshot/demo.gif)

### Add to your project
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
        compile 'com.github.uin3566:DragFooterView:v1.0.0'
    }
```

### Usage
1、add in xml like this **(Attention:it should have only one child view)**
```xml
    <com.fangxu.library.DragContainer
        android:id="@+id/drag_recycler_view"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="10dp"
        app:dc_bezier_threshold="100dp"
        app:dc_footer_height="15dp"
        app:dc_icon_drawable="@drawable/left"
        app:dc_icon_size="10dp"
        app:dc_reset_animator_duration="500"
        app:dc_text_event="释放查看"
        app:dc_text_normal="查看更多">

        <android.support.v7.widget.RecyclerView
            android:id="@+id/recycler_view"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:background="@android:color/white" />
    </com.fangxu.library.DragContainer>
```
2、in java code,add DragListener
```java
    DragContainer dragContainer = (DragContainer) findViewById(R.id.drag_image_view);
    dragContainer.setDragListener(new DragListener() {
        @Override
        public void onDragEvent() {
            //do whatever you want,for example skip to the load more Activity.
            Intent intent = new Intent(HomeActivity.this, ShowMoreActivity.class);
            startActivity(intent);
        }
    });
```

###Attributes
all of the attributes are listed below:  

|attribute|value type|defalut value| description|
| --- | --- | --- | --- |
|dc_icon_drawable| reference| None|the icon show in footer|
|dc_icon_size|dimension|15dp|the icon size show in footer|
|dc_text_normal|string|None|the text string show in footer while release will not trigger DragListener|
|dc_text_event| string| None|the text string show in footer while release will trigger DragListener|
|dc_text_size|dimension|10sp|the size of footer text|
|dc_text_color|color|0xff222222|the color of footer text|
|dc_text_icon_gap|dimension|4dp|the distance of footer icon and footer text|
|dc_footer_height|dimension|30dp|the thickness of the footer rectangle part|
|dc_footer_color|color|0xffcdcdcd|the color of footer background|
|dc_reset_animator_duration|integer|700|the reset animator duration in milliseconds|
|dc_drag_damp|float|0.5f|the drag damp,should be set in range (0,1],set it smaller will drag more difficultly|
|dc_bezier_threshold|dimension|120dp|if the drag distance bigger than it, the bezier path will not change any more|


###License
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
