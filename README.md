Docker Wordpress Child Theme Demo
=================================

这个文章非常好，看完基本上就明白了：

https://developer.wordpress.org/themes/advanced-topics/child-themes/

简单的说，想对某个theme进行扩展，可以不修改它，而是创建一个同名-child的目录，里面放上
style.css和functions.php文件。同时在admin后台启用该theme.

style.css文件比较重要，它的作用是定义该theme以及定位，但是它里面定义的css并不会覆盖parent，也不会自动load。
需要我们在functions.php里手动使用`wp_enqueue_scripts`加载。

functions.php里的内容，将最先被load，然后才是parent的functions.php，并且内容会被合并而非覆盖。
其它所有的文件，都是child会覆盖parent。

当我们想修改某个parent文件时，通常copy它到child，然后修改。

当需要load某个child theme中的文件，使用`get_stylesheet_directory()`。
load某个parent theme中的文件，使用`get_template_directory()`

本demo中的child theme位于：WordPress-5.3.2/wp-content/themes/twentytwenty-child

```
npm run up
```

当前登录wordpress的用户名和密码是：

```
freewind
123456
```

进入后台，启用twentytwenty-child，回到首页，可以看到我们添加的css效果。
