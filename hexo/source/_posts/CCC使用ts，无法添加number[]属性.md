---
title: CCC使用ts，无法添加number[]属性
categories: 随手记
tags: [CocosCreator,TypeScrip]
---

使用ts开发ccc的时候，发现
```
@property
key: number[] = [];
```
属性不会被ccc加载，多次尝试后，解决方法是：
```
@property({
    type: cc.Integer
})
key: [] = [];
```
官方手册中也有介绍，在 v1.10 包括之后的版本，Creator 对资源类型进行了部分调整，cc.Texture2D、cc.AudioClip、cc.ParticleAsset类型在ts中的声明一定要按照以下的格式进行声明：
```
@property({
    type: cc.Texture2D
})
texture: cc.Texture2D = null;

@property({
    type: cc.Texture2D
})
textures: cc.Texture2D[] = [];
```
number[]属性的问题，应该与此类似。