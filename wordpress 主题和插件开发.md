wordpress 主题和插件开发
====================

[TOC]

#WordPress模版层级

 - 见WordPress模版层级图

wordpress主题构成

模版文件__index.php/single.php/page.php/category.php/tag.php ...
样式文件__style.css ...
图片文件__images/ ...
缩略图片__screenshot.png (880px * 660px)
功能文件__functions.php
其他文件__javascript文件

# wordpress常用函数

## 引入标签 （6个）

+ get_header()
    - 在调用该函数的地方，引入header.php模版文件。
+ get_sidebar()
    - 在调用该函数的地方，引入sidebar.php模版文件。
+ get_footer()
    - 在调用该函数的地方，引入footer.php模版文件。
+ get_template_part()
    - 在一个模版文件中，引入另一个文件。
+ get_search_form()
    - 在模版文件中，调用搜索框代码，用户就可以看到搜索框。
+ comments_tamplate()
    - 引入评论框。



## 流程控制语句

条件语句

if(判断条件){语句;}else{语句;}
if(判断条件){语句;}else if(判断条件){语句;}else{语句;}

循环语句

while(判断条件){语句;}

## wordpress主循环

```php
<?php if(have_posts()) : while(have_posts()) : the_post; ?>
    循环体;
<?php endwhile; ?>
<?php endif; ?>
```

## wordpress模板标签

bloginfo()
wp_title()

the_title()
the_permalink()
the_content()
the_excerpt()
the_category()
the_tags()
the_author()
the_author_posts_link()
the_time()

comments_popup_link()
edit_post_link()
next_post_link()
previous_post_link()
next_posts_link()
previous_posts_link()



### bloginfo()

    + 描述：获取并显示你的wordpress站点的相关信息，主要是wordpress后台中用户--》个人资料，和设置--》常规中的数据信息
    + 用法：<?php bloginfo( $show ); ?>
    + 参数$show：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - name  显示站点标题
                    - description  显示站点副标题
                    - wpurl  显示wordpress地址(url)
                    - url  显示站点地址(url)
                    - admin_email  显示管理员邮箱地址
                    - charset  显示网页字符编码
                    - version  显示wordpress版本信息
                    - html_type  显示Content-Type
                    - text_direction  显示文本方向
                    - language  显示wordpress语言版本
                    - stylesheet_url  显示激活主题的主样式表的网址
                    - stylesheet_directory  显示激活主题的主题所在目录的网址
                    - template_url / template_directory  显示激活的主题所在的目录的网址
                    - pingback_url  显示pingback文件的网址
                    - atom_url  显示atom feed的网址
                    - rdf_url  显示rdf feed的网址
                    - rss_url  显示rss feed的网址
                    - rss2_url  显示rss2 feed的网址
                    - comments_atom_url  显示评论的atom feed网址
                    - comments_rss2_url  显示评论的rss2 feed的网址
            - 默认的值：name
    + 返回：无

### wp_title()

    + 描述：显示或调取页面的标题信息。
    + 用法：<?php wp_title( $sep, $display, $seplocation ); ?>
    + 参数$sep：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - 无限制
            - 默认的值：&raquo; (»)
    + 参数$display：
            - 是否可选：可选
            - 参数类型：布尔型
            - 可选值：
                    - true  直接显示调取的数据
                    - false  不显示
            - 默认的值：true
    + 参数$seplocation：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - left  分隔符在左侧
                    - rigth  分隔符在右侧
            - 默认的值：left
    + 返回：
            - 单篇信息页  -->  显示信息的标题
            - 日期存档页  -->  显示日期信息
            - 分类存档页  -->  显示分类名称
            - 作者存档页  -->  显示作者的公开名称

### the_title()

    + 描述：显示或者返回当前信息的标题，比如文章信息的标题、页面信息的标题
    + 用法：<?php the_title( $before, $after, $echo ); ?>
    + 参数$before：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - 无限制
            - 默认的值：无
    + 参数$after：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - 无限制
            - 默认的值：无
    + 参数$echo：
            - 是否可选：可选
            - 参数类型：布尔型
            - 可选值：
                    - true  直接显示标题
                    - false  不直接显示而是返回
            - 默认的值：true
    + 返回：
            - 如果$echo参数取值为true  没有返回值
            - 如果$echo参数取值为false  返回调用的标题

### the_permalink()

    + 描述：显示当前信息的网址。
    + 用法：<?php the_permalink(); ?>
    + 参数：没有任何参数
    + 返回：没有任何返回值

### the_content()

    + 描述：显示当前信息的内容，比如文章信息的内容、页面信息的内容
    + 用法：<?php the_content( $more_link_text, $stripteaser ); ?>
    + 参数$more_link_text：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - 无限制
            - 默认的值：(more...)
    + 参数$stripteaser：
    + 返回：无返回值

### the_excerpt()

    + 描述：调取在发布数据时填写的摘要信息。如果没有设置摘要信息，则从发布的正文中截取55各字符。
    + 用法：<?php the_excerpt(); ?>
    + 参数：无
    + 返回：无

### the_category()

    + 描述：显示当前文章所属的分类目录。
    + 用法：<?php the_category( $separator, $parents, $post_id ); ?>
    + 参数$separator：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - 无限制
            - 默认的值：空字符
    + 参数$parents：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - multiple
                    - single
            - 默认的值：空字符
    + 参数$post_id：
            - 是否可选：可选
            - 参数类型：整数型
            - 可选值：
                    - 整数值
            - 默认的值：false
    + 返回：无返回值

### the_tags()

    + 描述：显示当前信息所属的标签。
    + 用法：<?php the_tags( $before, $sep, $after ); ?>
    + 参数$before：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - 无限制
            - 默认的值：标签：
    + 参数$sep：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - 无限制
            - 默认的值：逗   号
    + 参数$after ：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - 无限制
            - 默认的值：无   值
    + 返回：无

### the_author()

    + 描述：显示当前文章的作者。
    + 用法：<?php the_author(); ?>
    + 参数：无
    + 返回：无

### the_author_posts_link()

    + 描述：显示作者存档页的超链接。
    + 用法：<?php the_author_posts_link(); ?>
    + 参数：无
    + 返回：无

### the_time()

    + 描述：显示文章发布的时间。
    + 用法：<?php the_time( $d ); ?>
    + 参数$d：
            - 是否可选：可选
            - 参数类型：字符串string
            - 可选值：
                    - Y  年
                    - m  月
                    - d  日
                    - h  时
                    - i  分
                    - s  秒
            - 默认的值：无
    + 返回：无

### comments_popup_link()

    + 描述：显示一个指向评论框的超链接，当用户点击这个超链接的时候，会自动打开应对的文章，并且自动跳转到评论框的位置。
    + 用法：<?php comments_popup_link( $zero, $one, $more, $css_class, $none ); ?>
    + 参数$zero：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：No Comments
    + 参数$one：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：1 Comment
    + 参数$more：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：% Comments
    + 参数$css_class：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：无
    + 参数$none：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：Comments Off
    + 返回：无

### edit_post_link()

    + 描述：显示一个编辑当前文章的超链接，用户点击之后直接进入到后台对文章进行编辑。
    + 用法：<?php edit_post_link( $link, $before, $after, $id ); ?>
    + 参数$link：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：__('Edit This')
    + 参数$before：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：无
    + 参数$after：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：无
    + 参数$id：
            - 是否可选：可选的
            - 参数类型：整数型
            - 可选值：
                    - 无限制
            - 默认的值：无
    + 返回：无

### next_post_link()

    + 描述：显示下一篇信息的链接（所谓下一篇，是指更新发布的信息）
    + 用法：<?php next_post_link( $format, $link, $in_same_term, $excluded_term, $taxonomy); ?>
    + 参数$format：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - ？？%link？？
            - 默认的值：%link &raquo;
    + 参数$link：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：%title
    + 参数$in_same_term：
            - 是否可选：可选的
            - 参数类型：布尔型
            - 可选值：
                    - true  显示的信息是属于同一分类下
                    - false  显示的信息包含所有分类
            - 默认的值：false
    + 参数$excluded_term：
            - 是否可选：可选的
            - 参数类型：字符串 或 数组
            - 可选值：
                    - 分类的ID  逗号隔开或数组形式
            - 默认的值：无
    + 参数$taxonomy：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 分类形式的名称
            - 默认的值：category
    + 返回：无

### previous_post_link()

    + 描述：此函数和next_post_link()函数对应，只是获取的是上一篇信息（更早发布的信息），用法完全相同。
    + 用法：<?php previous_post_link( $format, $link, $in_same_term, $excluded_term, $taxonomy); ?>
    + 参数：
    + 返回：无

### next_posts_link()

    + 描述：显示下一页信息。在wordpress后台，可以设置“博客页最多显示” 多少篇文章，比如10篇。
    + 用法：<?php next_posts_link( $label , $max_pages ); ?>
    + 参数$label：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：Next Page »
    + 参数$max_pages：
            - 是否可选：可选的
            - 参数类型：整数型
            - 可选值：
                    - 整数值
            - 默认的值：0  有几页就分几页
    + 返回：无

### previous_posts_link()

    + 描述：显示下一页信息。
    + 用法：
    + 参数：
            - 是否可选：可选的
            - 参数类型：字符串
            - 可选值：
                    - 无限制
            - 默认的值：« Previous Page
    + 返回：无





## wordpress主题功能

### 用到的函数：

    #### wp_head()

        + 描述：在网页元素</ head>标签前增加一些东西
        + 用法：<?php wp_head(); ?>
        + 参数：无
        + 返回：无

    #### add_theme_support()

        + 描述：允许主题或者插件，注册并开启wordpress某个主题特色功能。如果在主题中调用，该函数应该在functions.php中使用。
        + 用法：<?php add_theme_support( $feature, $arguments ); ?>
        + 参数$feature：$features代指哪像功能？因为add_theme_support()函数可以开启多项wordpress特色功能。所以你需要传递$features参数，让wordpress明确知道开启具体哪项功能。
                - 是否可选：必选的
                - 参数类型：字符串
                - 可选值：
                        - 'post-formats‘  文章形式
                        - 'post-thumbnails'  开启缩略图
                        - 'custom-background'  开启自定义背景
                        - 'custom-header'  开启自定义头部
                        - 'automatic-feed-links'  开启feed自动链接地址
                        - 'html5'  开启HTML5支持功能
                - 默认的值：无
        + 参数$arguments：$arguments代指更详细的参数。wordpress内置了几项特色功能，有些功能在开启时还需要向wordpress提供更多的参数。而且，开启不同的功能，参数$arguments的值各不相同……
                - 是否可选：可选的
                - 参数类型：数组
                - 可选值：
                        - 省    略
                - 默认的值：true
        + 返回：无

    #### has_post_thumbnail()

        + 描述：判断一篇文章是否设置了特色图像。
        + 用法：<?php has_post_thumbnail( $post_id ); ?>
        + 参数$post_id：$post_id 代指信息的编号（包括文章信息和页面信息）
                - 是否可选：可选的
                - 参数类型：整数型
                - 可选值：
                        - 编号值
                - 默认的值：当前文章编号
        + 返回：
                - true  如果文章存在特色图像
                - false  如果文章不存在特色图像


    #### the_post_thumbnail()

        + 描述：显示当前文章的特色图像。
        + 用法：<?php the_post_thumbnail( $size, $attr ); ?>
        + 参数$size：$size代指图像的尺寸。
                - 是否可选：可选的
                - 参数类型：字符串或数组
                - 可选值：
                        - 关键词   thumbnail | medium | large | full     尺寸可以在后台设置
                        - 尺寸值   array(宽度，高度)
                - 默认的值：post-thumbnail
        + 参数$attr：不建议改
        + 返回：无


    #### register_nav_menu()

        + 描述：开启导航菜单，让一个主题拥有导航菜单功能。
        + 用法：<?php register_nav_menu( $location, $description ); ?>
        + 参数$location：$location代指导航的位置，在开启导航时，给定此参数，可以设置多个位置的导航。方便你在调用（使用）导航时，知道调用哪个位置的导航
                - 是否可选：必填的
                - 参数类型：字符串
                - 可选值：
                        - 无限制
                - 默认的值：无
       + 参数$description：$description代指菜单的描述。此描述，会在后台中显示出来。
                - 是否可选：必填的
                - 参数类型：字符串
                - 可选值：
                        - 无限制
                - 默认的值：无
        + 返回：无


    #### wp_nav_menu()

        + 描述：显示在后台中创建的菜单项目。给定$theme_location参数，此函数则显示制定的菜单。如果给定的$theme_location不存在、或者没有指定菜单项目，则根据fallback_cb参数的规则显示内容。
        + 用法：<?php wp_nav_menu( $args ); ?>
        + 参数$args：$args代指一个数组。如果你不知道什么是数组，也没关系。你只需要这个参数比较特殊，传递这个参数时，需要写成:array(参数成员1=>参数成员1的值,参数成员2=>参数成员2的值，…………………………………);
                - 是否可选：必填的
                - 参数类型：数组
                - 可选值：
                        -
                - 默认的值：
                ```
                $defaults = array(
                  'theme_location'  => '',
                  'menu'            => '',
                  'container'       => 'div',
                  'container_class' => '',
                  'container_id'    => '',
                  'menu_class'      => 'menu',
                  'menu_id'         => '',
                  'echo'            => true,
                  'fallback_cb'     => 'wp_page_menu',
                  'before'          => '',
                  'after'           => '',
                  'link_before'     => '',
                  'link_after'      => '',
                  'items_wrap'      => '<ul id="%1$s" class="%2$s">%3$s</ul>',
                  'depth'           => 0,
                  'walker'          => ''
                );
                ```
        + 返回：
        - 如果$echo =true   无返回值
        - 如果$echo=false  有返回值



### 开启Feed自动链接

    + 简介：Feed让用户不用登录你的网站，也能查看到你网站的更新。向用户提供rss feed地址，用户拿到地址后添加到rss阅读器，一旦有更新，rss阅读器会立即提示
    + 使用：
            - 步骤一：头元素中添加wp_head()函数        php wp_head();
            - 步骤二：在功能文件中开启自动链接        add_theme_support( 'automatic-feed-links' );
            - 步骤三：在页面中添加feed链接地址        bloginfo('rss2_url');

### 开启缩略图功能

    + 简介：
    + 使用：
            - 步骤一：开启缩略图功能        add_theme_support('post-thumbnails', array('post', 'page'));
            - 步骤二：上传缩略图图片
            - 步骤三：调用缩略图图片         the_post_thumbnail( $size, $attr );

### 开启导航菜单功能

    + 简介：
    + 使用：
            - 步骤一：开启菜单功能   register_nav_menu()
            - 步骤二：设置菜单项目
            - 步骤三：调用导航菜单   wp_nav_menu( ... )；

### 开启侧边栏功能

    + 简介：
    + 使用：
            - 步骤一：
            - 步骤二：
            - 步骤三：