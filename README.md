# LubinBottomTabBar

   这是一个底部导航栏小控件，上部分是小图标，下部是文字，类似微信，有点击监听、定位设置等。
   This is a bottom navigation bar small control, the upper part of the small icon,the lower part of the text, similar to WeChat, click listen, location Settings, and so on.
 
## 快速使用

* gradle引用

```markdown
implementation 'com.lubin.layout.tabbar:lubinbottomtabbar:0.5.1'
```
## (一)单独使用LubinBottomTabBar

### 准备资源
 ** drawable:用于图标
```xml
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@drawable/ic_shopping_basket_black_24dp" android:state_selected="true" />
    <item android:drawable="@drawable/ic_shopping_basket_wrigth_24dp" />
</selector>
``` 
 ** string:底部图标下的文字 ‘name值自定义’
 ```xml
<resources>

·····
    
    <string name="bottom_bar_home">首页</string>
    <string name="bottom_bar_shoppping">商城</string>
    <string name="bottom_bar_mine">我的</string>
    <string name="bottom_bar_nearby">附近</string>
</resources>

```
 **color：文字改变颜色 ‘name值自定义’
 ```xml
 <resources>
 
 ······
 
    <color name="bottom_bar_txt_default">#999999</color>
    <color name="bottom_bar_txt_select">#00deff</color>
</resources>

```
### xml布局中添加

```xml
    <com.lubin.layout.tabbar.LubinBottomTabBar
        android:id="@+id/tab_bar"
        android:layout_width="match_parent"
        android:layout_height="45dp" />
```
### java（Activity或Fragment）中使用

```java
class MyActivyty{
    
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        //... ...            
    
        tabItems = new ArrayList<>();
        /**
        *  TabItem 添加资源，添加一个TabItem就是底部有一个icon
        */
        tabItems.add(new TabItem(R.string.us, R.drawable.ic_01,new int[]{R.color.colorAccent,R.color.colorPrimary}, ""));
        /**
        * 获取lubinbottomtabbar后，然后赋值 
        */
        lubinbottomtabbar.initData(tabItems, this); 
        
    }
}

```

 **  LubinBottomTabBar
 
 ```markdown
    /**
     * 必须最先调用
     * It has to be called first
     *
     * @param tabList  数据源
     * @param listener 事件回调
     */
    public LubinBottomTabBar initData(List<TabItem> tabList, OnTabBarListener listener)
    
    /**
     * 设置选中项
     * Set the currently selected tabBar item.
     *
     * @param item Item index to select
     */
    public LubinBottomTabBar setCurrentItem(int item)

```
 ** TabItem（子项资源赋值）
 
```markdown
    /**
     * 加载数据
     *
     * @param txtItem 文本资源id
     * @param icItem  图片资源id
     * @param extra   额外信息
     */
    public TabItem(@StringRes int txtItem, @DrawableRes int icItem, String extra)

    /**
     * 加载数据
     *
     * @param txtItem  文本资源id
     * @param icItem   图片资源id
     * @param txtColor 文字颜色
     * @param extra    额外信息
     */
    public TabItem(@StringRes int txtItem, @DrawableRes int icItem, @ColorRes int[] txtColor, String extra)
    
    /**
     * 加载数据
     *
     * @param txtItem 文本资源id
     * @param icItem  图片资源id
     * @param txtSize 文字大小
     * @param extra   额外信息
     */
    public TabItem(@StringRes int txtItem, @DrawableRes int icItem, @Size float txtSize, String extra) 

    /**
     * 加载数据
     *
     * @param txtItem  文本资源id
     * @param icItem   图片资源id
     * @param txtSize  文字大小
     * @param txtColor 文字颜色
     * @param extra    额外信息
     */
    public TabItem(@StringRes int txtItem, @DrawableRes int icItem, @Size float txtSize, @ColorRes int[] txtColor, String extra)
```