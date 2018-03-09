
# 学科网公共头部
![](http://xkw-18913.oss-cn-hangzhou.aliyuncs.com/wiki/QQ20180309-161110@2x.png)  

```html
<script src="http://www.zxxk.com/service/js/header.js" type="text/javascript" charset="utf-8"></script>
```


# 右侧顶部按钮
![](http://xkw-18913.oss-cn-hangzhou.aliyuncs.com/wiki/panel.png)
```html
<div class="fn-rt func-icons">
	<a href="http://www.zxxk.com/wxt/v3/source/center" target="_blank">
	    <i class="iconfont icon-wangxiaotong"></i>
	    <span>网校通</span>
	</a>
	<a href="http://www.zxxk.com/OnlinePay/" target="_blank">
	    <i class="iconfont icon-chongzhi"></i>
	    <span class="charge-btn">充值<span class="__web-inspector-hide-shortcut__"></span></span>
	</a>
	<a href="http://user.zxxk.com/default.aspx?new=UpLoadFile.aspx" target="_blank">
	    <i class="iconfont icon-shangchuan2"></i>
	    <span class="earn-cash-tips">
	        上传
	        
	    </span>
	</a>
</div>
```

# 购物篮
![](http://xkw-18913.oss-cn-hangzhou.aliyuncs.com/wiki/QQ20180309-115347@2x.png)    
```html
<div class="source-bucket-wrap" id="divSoftCart">
    <div class="source-bucket">
        <i class="iconfont icon-gouwuche"></i>
        <a href="http://cart.zxxk.com/" target="_blank"><span class="text-color">资源篮</span></a>
        <label name="softCartCount" class="number">0</label>
    </div>
    <div style="height: 80px; padding-top: 0px; margin-top: 0px; padding-bottom: 0px; margin-bottom: 0px;" class="zyl_list" id="softCart">
        <ul id="softCartList" style="display: none;"></ul>
        <div id="cartbtn" class="zyl_btn" style="display: none;">
            <div class="all">
                共
                <span name="softCartCount">0</span>份资料
            </div>
            <input id="clearButton" type="button" value="清空">
            <input type="button" value="全部下载" onclick="window.open('http://cart.zxxk.com/')">
        </div>
        <div id="cartempty" class="no_res" style="">资源篮中还没有资源，赶紧挑选吧！</div>
    </div>
</div>
```

# 竖分割线
![](http://xkw-18913.oss-cn-hangzhou.aliyuncs.com/wiki/QQ20180309-161815@2x.png)

```html
<span class="vertical-line"></span>
```

# 首页楼层标题和导航
![](http://xkw-18913.oss-cn-hangzhou.aliyuncs.com/wiki/QQ20180309-162146@2x.png)  

```html
<span class="title-tips">名校资源</span>
<ul class="row-top-nav">
        <li class="mxzy-province areaid14">苏</li>
        <li class="mxzy-province areaid4">沪</li>
        <li class="mxzy-province areaid16">粤</li>
        <li class="mxzy-province areaid10">鲁</li>
        <li class="mxzy-province areaid13">浙</li>
        <li class="mxzy-province areaid2 current">京</li>
        <li class="mxzy-province areaid21">湘</li>
        <li class="mxzy-province areaid22">川</li>
        <li class="mxzy-province areaid17">闽</li>
        <li class="mxzy-province areaid12">皖</li>
        <li class="mxzy-province areaid6">冀</li>
        <li class="mxzy-province areaid19">豫</li>
        <li class="mxzy-province areaid20">鄂</li>
        <li class="mxzy-province areaid15">赣</li>
        <li class="mxzy-province areaid25">陕</li>
        <li class="mxzy-province areaid5">渝</li>
        <li class="mxzy-province areaid30">桂</li>
        <li class="mxzy-province areaid11">晋</li>
        <li class="mxzy-province areaid9">吉</li>
        <li class="mxzy-province areaid7">辽</li>
        <li class="mxzy-province areaid8">黑</li>
        <li class="mxzy-province areaid29">蒙</li>
        <li class="mxzy-province areaid28">宁</li>
        <li class="mxzy-province areaid32">新</li>

<li class="more-btn" style="margin-right: 0"><a href="http://mingxiao.zxxk.com/" target="_blank" more="1">更多</a></li>
</ul>
```

# 楼层快捷导航
![](http://xkw-18913.oss-cn-hangzhou.aliyuncs.com/wiki/QQ20180309-162813@2x.png)  

html：
```html
<div class="gofloor" style="display: block;">
    <p target="djtj" class="">推荐</p>
    <p target="mxzy" class="">名校</p>
    <p target="jpzy" class="">精品</p>
    <p target="spzy" class="">视频</p>
    <p target="zxzr">最新</p>
    <p target="jxzj" class="">专辑</p>
    <p target="jyzx" class="">资讯</p>
    <p target="hzxfc" class="current">合作校</p>
</div>
```
事件处理程序：
```javascript
/**
 * 左侧导航反向定位事件
 */
quickNavHandler: function() {
    //滚动下来350左侧快捷菜单才显示
    var stp = $(this).scrollTop()
    stp > 350 ? $('.gofloor').fadeIn(300) : $('.gofloor').fadeOut(300);
    //反向定位
    var floorNames = ['djtj', 'mxzy', 'jpzy', 'spzy', 'jxzj', 'jyzx', 'hzxfc'];
    $(floorNames).each(function(index, cardName) {
        $('.section-' + cardName + '').offset() &&
            stp >= $('.section-' + cardName).offset().top &&
            $('.gofloor [target=' + cardName + ']').addClass('current').siblings().removeClass('current');
    })
}

/**
 * 左侧快捷导航点击
 */
initLeftNav: function() {
    var self = this;
    $('.gofloor p').click(function() {
        $(window).unbind('scroll', self.quickNavHandler);
        var cardName = $(this).attr('target');
        $(this).siblings().removeClass('current');
        $(this).addClass('current');
        $('body,html').animate({
            scrollTop: $('.section-' + cardName).offset().top
        }, 700, 'swing');
        setTimeout(function() {
            $(window).scroll(self.quickNavHandler);
        }, 800);
    });
}
```