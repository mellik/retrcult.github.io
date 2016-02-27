---
layout: post
title: CSS Object-fit & Object-position
tags: [CSS]
---

`object-fit`和`object-position`使开发人员可以操作img或video中的内容，类似于我们可以用`background-position`和`background-size`操作背景内容一样。

{% highlight css %}
{% endhighlight %}

<!--more-->

object-fit
-------

该属性定义一个元素，如img，如何适应容器的宽度和高度。我们可以用`object-fit`告诉内容以各种方式填充容器，如“保存该长宽比！” 或“向上伸展，尽可能多的占用空间！”

![example image]({{ site.baseurl }}/images/2016/02/picjumbo_HNCK8936.jpg)

这张图片的大小为 500 x 334。如果我们这样给图片设置样式...

<div id="example01" class="display-code">
<style type="text/css" contenteditable>
#example01 img {
  width: 200px;
  height: 300px;
  // object-fit: cover;
}

</style>

  <p>...最后图片失真，因为图片为了适应容器已经被压扁。</p>

  <p><img src="/images/2016/02/picjumbo_HNCK8936.jpg"></p>
</div>

当我们改变了img的高度和宽度时，img的内容将占用我们所创建容器的所有可用空间，从而破坏了图片原本的长宽比。

为了保持图像的长宽比，同时也可以填充空间，我们可以使用`object-fit`（取消👆注释）。

让我们看另外一个案例:

在这里有两个图像，我们希望他们分别占据浏览器50%的宽度(这样他们就可以并排)，高度为100％。

问题是，当我们调整浏览器的大小时，就会改变图像的宽高比例，也就是会产生各种各样奇怪的现象。相反，我们希望就像前面的演示的一样，永远保持一样的宽高比例，其实我们完全也可以使用相同的办法。`object-fit:cover`就可以轻松的实现！

<div id="example02" class="display-code">
<style type="text/css" contenteditable>
#example02 img {
  float: left;
  width: 50%;
  height: 300px;
  object-fit: cover;
}

</style>

  <p class="clearfix">
    <img src="/images/2016/02/picjumbo_HNCK8953.jpg">
    <img src="/images/2016/02/picjumbo_HNCK8963.jpg">
  </p>
</div>



object-position
-------

我们将使用之前相同的图像以及使用如下的样式设置：

{% highlight css %}
img {
  background: blue;
  height: 200px;
  object-fit: none;
}
{% endhighlight %}

这里有两点需要注意的地方：为了使`object-position`能正常工作，我们需要声明一下图像尺寸。我们还需要将`object-fit`设置为none，以*避免默认情况下，图像并没填满整个容器*。这样做很有意义，因为即使你不声明，图像上`object-fit`属性也会*默认为fill*。

说到默认值，即使没有声明，`object-position`属性也会在水平和垂直方向上平分：

{% highlight css %}
object-position: 50% 50%;
/* even if we dont declare this the image will still be centered */
{% endhighlight %}

第一个值表示图像左右移动，第二个值表示上下移动。我们可以用下面这些的值进行演示：


<div id="example03" class="display-code">
<style type="text/css">
#example03 .row {
  margin: 15px 0;
  resize: both;
}
#example03 figure {
  display: inline-block;
  width: 40%;
  margin-right: 3%;
  max-width: 300px;
}
#example03 img {
  background: #3b3c3e;
  height: 210px;
  object-fit: none;
}
#example03 .image--with-background-image {
  background-image: url(/images/2016/02/picjumbo_HNCK8953.jpg);
}
</style>

  <div class="">
    <div class="row">
      <figure>
        <img src="/images/2016/02/picjumbo_HNCK8936.jpg">
        <figcaption>original image<br>(w/ background-color)</figcaption>
      </figure>
    </div>
    <div class="row">
      <figure><img class="image--center" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--center {
  object-position: 50% 50%;
}

</style></figure>
      <figure><img class="image--top-left" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--top-left {
  object-position: 0 0;
}

</style></figure></div>
    <div class="row">
      <figure><img class="image--bottom-left" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--bottom-left {
  object-position: 0% 100%;
}

</style></figure>
      <figure><img class="image--bottom-right" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--bottom-right {
  object-position: 100% 100%;
}

</style></figure></div>
    <div class="row">
      <figure><img class="image--up" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--up {
  object-position: 50% 120%;
}

</style></figure>
      <figure><img class="image--down" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--down {
  object-position: 50% -20%;
}

</style></figure></div>
    <div class="row">
      <figure><img class="image--left" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--left {
  object-position: 120% 50%;
}

</style></figure>
      <figure><img class="image--right" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--right {
  object-position: -20% 50%;
}

</style></figure></div>
    <div class="row">
      <figure><img class="image--with-background-image" src="/images/2016/02/picjumbo_HNCK8936.jpg">
<style type="text/css" contenteditable>
.image--with-background-image {
  object-position: 160% 90%;
}
</style></figure></div>
  </div>

</div>


