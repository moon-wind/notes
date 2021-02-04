## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/moon-wind/notes/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/moon-wind/notes/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.

# guacamole

标签（空格分隔）： vnc ssh rdp

---

###配置阿里云加速器
[地址：https://dev.aliyun.com](https://dev.aliyun.com)

<!-- sudo docker run --name some-guacamole     --link some-guacd:guacd             -e MYSQL_HOSTNAME=127.0.0.1 -e MYSQL_DATABASE=guacamole_db -e MYSQL_USER=guacadmin -e  MYSQL_PASSWORD=123456    -d -p 8080:8080 guacamole/guacamole -->

###Running guacd for use by the Guacamole Docker image
>docker run --name some-guacd -d guacamole/guacd

###Initializing the MySQL database
>docker pull mysql

>sudo docker run --name some-mysql -d -p 33060:3306 -e mysqld  -e MYSQL_ROOT_PASSWORD=root mysql
(mysqld #启动mysql服务   MYSQL_ROOT_PASSWORD)

>docker run --rm guacamole/guacamole /opt/guacamole/bin/initdb.sh --mysql > initdb.sql(导入脚本配置数据库)

###Connecting Guacamole to MySQL
>docker run --name some-guacamole \
    --link some-guacd:guacd         \
    --link some-mysql:mysql        \
    -e MYSQL_DATABASE=guacamole_db \
    -e MYSQL_USER=root \
    -e MYSQL_PASSWORD=root\
    -d -p 8080:8080 guacamole/guacamole
