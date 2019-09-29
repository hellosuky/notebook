### wamp面对同于局域网使用手机端浏览本地开发页面

---

之前在公司反复提交到qa使我头都秃了，因为我们知道反复的提交对git分支其实是毫无用处的，甚至我们可以认为是“不明智的开发”，那这时候我们就想，那我能在本地的同一个局域网中能够进行合适的访问吗？答案是肯定的。



#### 不能够通过www.abc.com这种方式来网页的访问

---

首先我们应该明确一点：对于我们本地的开发环境，我们不是访问某个域名，而是应该访问某个**主机**。意思即是我们访问本地开发环境应该是找到我们的本地环境的主机，然后通过虚拟的服务器，使我们能够达到访问主机内部文件夹的目的。



#### wamp配置允许同一局域网的访问

---

找到`httpd.conf`中以下字段

```
 Options +Indexes +FollowSymLinks +Multiviews

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   AllowOverride FileInfo AuthConfig Limit
    #
    AllowOverride all

    #
    # Controls who can get stuff from this server.
    #
#   onlineoffline tag - don't remove
</Directory>
```

在`#onlineoffline tag -don't remove`后面跟上` Require all granted`即可开放同一局域网浏览器均可访问本主机的权利



#### 多个地址配置无法显示我们网页

---

很多时候我们一个wamp里面其实会有多个网站在其中，那这时候我们应该怎么办？那对于我来说，只有一个网站需要我在手机端进行测试，所以我是通过修改默认的地址来达到目的。

具体说来，在`httpd.conf`中修改

```
DocumentRoot "D:/web/shumen.com/h5/web" 
RewriteEngine on
RewriteRule ^([^\.]*)$ /index.php$1
<Directory "D:/web/shumen.com/h5/web">
    #
    # Possible values for the Options directive are "None", "All",
    # or any combination of:
    #   Indexes Includes FollowSymLinks SymLinksifOwnerMatch ExecCGI MultiViews
    #
    # Note that "MultiViews" must be named *explicitly* --- "Options All"
    # doesn't give it to you.
    #
    # The Options directive is both complicated and important.  Please see
    # http://httpd.apache.org/docs/2.4/mod/core.html#options
    # for more information.
    #
    Options +Indexes +FollowSymLinks +Multiviews

    #
    # AllowOverride controls what directives may be placed in .htaccess files.
    # It can be "All", "None", or any combination of the keywords:
    #   AllowOverride FileInfo AuthConfig Limit
    #
    AllowOverride all

    #
    # Controls who can get stuff from this server.
    #
#   onlineoffline tag - don't remove
    Require all granted
</Directory>
```

里面`DocumentRoot`和`Directory`的文件路径修改成我们网站的路径，这样默认就能够直接访问到我们的网站，不然地话，我们只能够修改本地的`hosts`才能够达到目的了。