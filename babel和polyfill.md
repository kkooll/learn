# polyfill
## 1. 什么是polyfill
polyfill可以理解是抹平差异化。如果我们调用的某个原生api在这个环境下不支持，我们就会引用polyfill来补齐。

## 2. 按需polyfill
我们在引入polyfill的时候，可能这个能力或者说api我们的环境原本就支持，这部分的加载就没有必要。

### 如何实现按需polyfill
通过preset-env来实现js和css的polyfill的按需引入。
1. 针对js使用@babel/preset-env，一般是按需做语法转换，按需引入polyfill。
2. 针对css使用postcss-reset-env，css的polyfill一般就是prefix。

### 按需polyfill原理
1. js部分
在配置时可以指定目标版本
```json
{
    "preset": [
        ["@babel/preset-env", {
            "target": "> 0.25%, not dead"
        }]
    ]
}
````
- targets是browserslist的查询字符串，可以解析字符串对应的浏览器版本
- babel在@babel/compat-data包中维护了各特性个版本的支持情况的一个数据库
- 找到不支持的，只针对不支持的做语法转换和引入
2. css部分
和js基本一致，配置有点不同，css是根据cssdb的数据库（来源：caniuse）
```js
postcssPresetEnv({browser: 'last 2 version2'})
```


# babel
## 1. 什么是babel
## 2. 有了babel还需要polyfill吗？
## 



# 参考链接
1. [按需 polyfill 是怎么实现的？](https://mp.weixin.qq.com/s/DTnNv6R-WHHfWwLkyRzPqA)
2. [polyfill为何物](https://juejin.cn/post/6844903549768302606)
3. [用了babel还需要polyfill吗？？？](https://juejin.cn/post/6845166891015602190)
4. [关于babel的详细解读(精华又通俗)](https://juejin.cn/post/6844904199554072583)
