---
layout: post
title: Comm(ent|it)评论系统的用法
description: Comm(ent|it)是一种用于博客的评论系统，用来代替被墙的disqus，缅怀你，disqus君
category: blog
---
#前言

缅怀你，disqus君。

#```Comm(ent|it)```的出现
在你被墙之后，只能寻找另一个评论系统代替你。免费的国内评论系统的尿性只能呵呵了，所以找到了```Comm(ent|it)```。

它将用户的评论commit到博客的github上，只有博主同意并且将数据合并，评论才能出现在博客上。


##下面是正戏了，让大家学习一下怎么使用```Comm(ent|it)```
首先你应该将官网的代码复制到你的文章结尾,可以从官方的代码看出，作者使用了js和python的语法。你必须登陆之后才能评论，它目前貌似只支持github,tw和facebook的账号。
然后就是正文了：
  使用```Comm(ent|it)```也还是比较简单的，就是使用了github的pull request加上merge，将新评论作为一个新的pull request向你的博客请求，当你在github中看到这个新的请求，你就由自己的喜好去选择是否让这个评论merge进入你的博客。之后你就可以看到这个新鲜出炉的评论出现在你的博客了。
<noscript>Please enable JavaScript to view the comment form powered by <a href="https://commentit.io/">Comm(ent|it)</a></noscript>
<div id="commentit"></div>
<script type="text/javascript">
  /** CONFIGURATION VARIABLES **/
  var commentitUsername = 'ioloveuu';
  var commentitRepo = 'ioloveuu/ioloveuu.github.io';
  var commentitPath = '{{ page.path }}';

  /** DON'T EDIT FOLLOWING LINES **/
  (function() {
      var commentit = document.createElement('script');
      commentit.type = 'text/javascript';
      commentit.async = true;
      commentit.src = 'https://commentit.io/static/embed/dist/commentit.js';
      (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(commentit);
  })();
</script>
  {%if page.comments %}
  {% assign sorted_comments = (page.comments | sort: 'date') %}
{% endif %}
{% for c in sorted_comments %}
  <div class="media">
    <div class="media-left">
      <img src="{{ c.author.picture }}" alt="{{ c.author.displayName}}" height="73" width="73">
    </div>
    <div class="media-body">
      <p class="text-muted">
        <a href="{{ c.author.url }}">{{ c.author.displayName }}</a>
        on {{ c.date | date_to_string }}
      </p>
      <p>{{ c.content | newline_to_br }}</p>
    </div>
  </div>
{% else %}
  There are no comments on this post.
{% endfor %}
