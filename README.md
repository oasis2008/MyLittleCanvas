# MyLittleCanvas

You find canvas hard to use ? try MyLittleCanvas :)
Don't work with canvas methods, use objects instead !

For example, to add a custom underline on a textview

[![gif](https://raw.githubusercontent.com/florent37/MyLittleCanvas/master/medias/textview.png)](https://github.com/florent37/MyLittleCanvas)

```java
public class UnderlinedTextView extends android.support.v7.widget.AppCompatTextView {

    //define your canvas shapes
    final RoundRectShape roundRectShape = new RoundRectShape();

    public UnderlinedTextView(Context context, AttributeSet attrs, int defStyleAttr) {
        super(context, attrs, defStyleAttr);

        roundRectShape
                .setCorderRadius(10)
                .setColor(Color.parseColor("#3F51B5"));
    }

    @Override
    protected void onSizeChanged(int w, int h, int oldw, int oldh) {
        super.onSizeChanged(w, h, oldw, oldh);

        //customize your shapes
        roundRectShape
                .setWidth(w)
                .setHeight(10)
                .alignBottom(h);
    }

    @Override
    protected void onDraw(Canvas canvas) {
        super.onDraw(canvas);
        //and finally draw
        roundRectShape.onDraw(canvas);
    }
}
```

<a href='https://ko-fi.com/A160LCC' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi1.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

[ ![Download](https://api.bintray.com/packages/florent37/maven/mylittlecanvas/images/download.svg) ](https://bintray.com/florent37/maven/mylittlecanvas/_latestVersion)

```java
dependencies {
    compile 'com.github.florent37:mylittlecanvas:(lastversion)'
}
```

# Implementation

# Shapes

- RectShape
- RoundRectShape
- TextShape
- LineShape
- DrawableShape
- PathShape
- CircleShape

# Methods

```java
.setColor(int)
.setWillNotDraw(boolean)
.getCenterX() / .getCenterY()
.getHeight() / .getWidth()

//rect / roundRect
.setRect(left, top, left, bottom)
.setLeft/Right/Top/Bottom(value)
.alignLeft/Right/Top/Bottom(value / shape)
.below(shape)
.above(shape)
.setCorderRadius(corner)
.marginLeft/Right/Top/Bottom(value / shape)

//text
.setText(text)
.setTextSizePx(size)
.setTypeface(typeface)
.centerIn(rectShape)
.configureH(minX, maxX)
.centerVertical(minY, maxY)
```

# Graph Sample

[![gif](https://raw.githubusercontent.com/florent37/MyLittleCanvas/master/medias/graph.gif)](https://github.com/florent37/MyLittleCanvas)

Complete file, with all shaped and motion event manager

https://github.com/florent37/MyLittleCanvas/blob/master/app/src/main/java/canvastoolbox/florent37/github/com/canvastoolbox/MyTreeView.java

```java
public class MyTreeView extends View {

    //define your canvas shapes
    ...
    RoundRectShape childLeft;
    TextShape textChildLeft;
    LineShape lineParentChildLeft;
    ...

    public MyTreeView(Context context, @Nullable AttributeSet attrs, int defStyleAttr) {
            super(context, attrs, defStyleAttr);

            //customize your shapes

            ...
            childLeft.setCorderRadius(10)
                    .setColor(Color.parseColor("#2196F3"));
            textChildLeft.setColor(Color.WHITE)
                    .setTextSizePx(40);
            lineParentChildLeft.setStrokeWith(3)
                    .setColor(Color.parseColor("#3E3E3E"));
            ...
    }

    @Override
        protected void onSizeChanged(int w, int h, int oldw, int oldh) {
            super.onSizeChanged(w, h, oldw, oldh);

            //setup your shapes
            childLeft.setLeft(40)
                            .setWidth(200)
                            .below(parent) //another shape
                            .marginTop(250)
                            .setHeight(100);

            textChildLeft.setText("childLeft");
            textChildLeft
                    .setAlignment(Layout.Alignment.ALIGN_CENTER)
                    .centerIn(childLeft);

            lineParentChildLeft
                    .start(parent.getCenterX(), parent.getBottom())
                    .end(childLeft.getCenterX(), childLeft.getTop());
        }

        @Override
        protected void onDraw(Canvas canvas) {
            super.onDraw(canvas);

            ...
            //draw your shapes
            childLeft.onDraw(canvas);
            textChildLeft.onDraw(canvas);
            lineParentChildLeft.onDraw(canvas);
            ...
        }
}
```

# Credits

Author: Florent Champigny [http://www.florentchampigny.com/](http://www.florentchampigny.com/)

Blog : [http://www.tutos-android-france.com/](http://www.www.tutos-android-france.com/)

<a href="https://play.google.com/store/apps/details?id=com.github.florent37.florent.champigny">
  <img alt="Android app on Google Play" src="https://developer.android.com/images/brand/en_app_rgb_wo_45.png" />
</a>
<a href="https://plus.google.com/+florentchampigny">
  <img alt="Follow me on Google+"
       src="https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/gplus.png" />
</a>
<a href="https://twitter.com/florent_champ">
  <img alt="Follow me on Twitter"
       src="https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/twitter.png" />
</a>
<a href="https://www.linkedin.com/in/florentchampigny">
  <img alt="Follow me on LinkedIn"
       src="https://raw.githubusercontent.com/florent37/DaVinci/master/mobile/src/main/res/drawable-hdpi/linkedin.png" />
</a>


License
--------

    Copyright 2017 Florent37, Inc.

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
