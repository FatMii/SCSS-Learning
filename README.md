# SCSS-Learning

# Scss 和 Sass

Sass 从第三代开始，放弃了缩进式风格，并且完全向下兼容普通的 CSS 代码，这一代
的 Sass 也被称为 Scss

# 文档

单文件编译可以在下面的网站进行操作，多文件编译见下下节，中文文档缺失的东西挺多的，有条件的可以翻看英文文档。

中文文档：www.sass.hk

英文文档：sass-lang.com/documentati

CSS 转 Scss：www.sass.hk/css2sass

Scss 转 CSS：www.sassmeister.com

# Sass 版本

1. Dart Sass，用 Dart 语言写的 sass 实现，于 2016 年 11 月 1 日发布 alpha 版本，版本 1.23.0 之后完全支持模块化机制。

2. libSass 也就是俗称的 node-sass，用 c/c++实现的 sass 版本，使用非常广泛。node-sass 是绑定了 libsass 的 nodejs 库，可以极快的将.scss 文件编译为.css 文件，这个安装过程……，懂的都懂，官方也不推荐再使用了。

3. Ruby Sass，是最初的 Sass 实现，但是 2019 年 3 月 26 日被停止了，以后也不会再支持，使用者需要迁移到别的实现上

4. 中文文档的安装教程是 Ruby Sass，个人推荐使用 npm 安装 Dart Sass，这也是官方推荐的方式。

# 安装步骤

## 安装命令

```
npm install -g sass
```

## 目录结构

```
code
    --css
        --index.scss
    --dist
```

## 监听运行

```
使用命令行操作，监听文件夹下的scss文件并输出为css文件，如果是webpack项目，则需要使用sass-loader。

sass --style=expanded  -w css:dist --no-source-map
```

# 输出格式

```
scss提供了四种输出格式，在命令行中使用 --style 选项进行设置，在Live Sass Compiler中配置format参数。

「注：」dart sass只支持expanded和compressed。

sass --watch style.scss:style.css --style compressed
```

## <center> :nested</center>

nested 是 scss 默认的输出格式，选择器与属性等单独占用一行，缩进量与 scss 文件中一致，「每行的缩进量反映了其在嵌套规则内的层数」。

```
#main {
 color: #fff;
 background-color: #000; }
 #main p {
   width: 10em; }

.p {
 font-size: 10em;
 font-weight: bold;
 text-decoration: underline; }
```

## <center> :expanded</center>

expanded 输出像是我们平常手写的样式，选择器、属性等各占用一行，属性根据选择器缩进，而选择器不做任何缩进。

```

#main {
 color: #fff;
 background-color: #000;
}
#main p {
 width: 10em;
}

.p {
 font-size: 10em;
 font-weight: bold;
 text-decoration: underline;
}
```

## <center> :compact</center>

compact 会将每条 css 规则归纳为一行。嵌套过的选择器在输出时没有空行，不嵌套的选择器会输出空白行作为分隔符。

```

#main { color: #fff; background-color: #000; }
#main p { width: 10em; }

.p { font-size: 10em; font-weight: bold; text-decoration: underline; }

```

## <center> :compressed</center>

compressed会删除所有无意义的空格、空白行、以及注释，力求将文件体积压缩到最小，同时也会做出其他调整，比如会自动替换占用空间最小的颜色表达方式。

```
#main{color:#fff;background-color:#000}#main p{width:10em}.p{font-size:10em;font-weight:bold;text-decoration:underline}

```
