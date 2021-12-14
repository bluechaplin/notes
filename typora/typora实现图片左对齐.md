# typora实现图片左对齐

## 一、前言

`typora`是一款非常好用的markdown编辑器，但是经常使用的小伙伴应该发现一个问题，就是不管在什么主题下，图片的显示都是居中的，当你的图片裁剪不是很整齐的时候，看起来就很别扭:disappointed_relieved:，我们希望它可以实现左对齐

## 二、实现方式

每个主题都会有个样式文件，比如`fluent`主题就会有个`fluent.css`，我们在`css`文件的末尾加上一段样式文件就可以实现图片左对齐啦

样式代码

```css
/* ---- 图片 左对齐 S -------------------------------------------- */
p > .md-image:only-child:not(.md-img-error) img, p > img:only-child {
    display: block;
    margin: inherit;
}
/* ---- 图片 左对齐 E -------------------------------------------- */
```

## 三、效果

![image-20211215013711160](https://raw.githubusercontent.com/bluechaplin/image-repository/master/Dec.2021/202112150137279.png)

我们可以看到，图片已经实现了左对齐:smirk:

