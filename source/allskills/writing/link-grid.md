---
title: 链接网络
comments: false
---



## 用法

```jinja
{% linkgrid [image] [delimiter] [comment] %}
{% endlinkgrid %}
```

或

```jinja
{% lg [image] [delimiter] [comment] %}
{% endlg %}
```

 - `[image]`     : 默认图片的 URL 地址。
 - `[delimiter]` : 如果给出了可选的分隔符参数，则将其解释为每行中项的分隔符。
 - `[comment]`   : 如果给出了可选的注释参数，则将其解释为注释出一行的符号。

## 例子

```jinja
{% linkgrid %}
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
% Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
{% endlinkgrid %}
```

{% linkgrid %}
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
% Theme NexT | https://theme-next.js.org/ | Stay Simple. Stay NexT. | /images/apple-touch-icon-next.png
{% endlinkgrid %}

```jinja
{% lg /images/apple-touch-icon-next.png , %}
Theme NexT , https://theme-next.js.org/ , Stay Simple. Stay NexT. , /images/apple-touch-icon-next.png
Theme NexT , https://theme-next.js.org/ , Stay Simple. Stay NexT. , /images/apple-touch-icon-next.png
Theme NexT , https://theme-next.js.org/ , Stay Simple. Stay NexT. , /images/apple-touch-icon-next.png
% Theme NexT , https://theme-next.js.org/ , Stay Simple. Stay NexT. , /images/apple-touch-icon-next.png
{% endlg %}
```

{% lg /images/apple-touch-icon-next.png , %}
Theme NexT , https://theme-next.js.org/ , Stay Simple. Stay NexT. , /images/apple-touch-icon-next.png
Theme NexT , https://theme-next.js.org/ , Stay Simple. Stay NexT. , /images/apple-touch-icon-next.png
Theme NexT , https://theme-next.js.org/ , Stay Simple. Stay NexT. , /images/apple-touch-icon-next.png
% Theme NexT , https://theme-next.js.org/ , Stay Simple. Stay NexT. , /images/apple-touch-icon-next.png
{% endlg %}