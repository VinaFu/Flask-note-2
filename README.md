# Flask-note-2

1) HTTP

          http://127.0.0.1:5000
          意义：整个为本地IP.127.0.0.1= local machine， localhost；5000 = 本地portal

          On most machines localhost and 127.0.0.1 are functionally identical. But localhost is a label for the IP address and not the address itself. Localhost could be pointed at different IP addresses.
          
2)DEBUG模式+get and 404/200 -- terminal

          一个“/”表示主页，“/about”表示之后一页的内容。这就是写路径呀！

          改模式，需要在terminal里面关闭（control+c），然后重新run。
          新页面：control+右键： view page source，可以见代码.
          如果每次都要打开新的代码则会非常麻烦，所以在debug模式下进行。terminal里面/blog% export FLASK_DEBUG=1.
          之后我再修改文本内容，页面刷新即可改变。不用去terminal重新。
          
          更快的方式：
          if __name__=="__main__":
              app.run(debug=True)
              # 在terminal里面直接叫名字就可以开启debug模式

          "GET / HTTP/1.1" 200 -
          每一次出现的是上面的指令。200代表成功
          
          "GET /about HTTP/1.1" 404 -
          404表示页面不存在。
          
          "GET /home HTTP/1.1" 200 -
          "GET /about HTTP/1.1" 200 -
          你去找谁，谁就会出来：home，about
          
3）flaskblog.py - python

          from flask import Flask, render_template, url_for
          app = Flask(__name__) 
          —— 要外来使用/引用的东西放在天上
          
          posts = [
              {
                  "author":"Vina Fu",
                  "title":"Blog Post 1",
                  "content":"First post content",
                  "date_posted":"August 23,2022"
              },
              {
                  。。。
              }
          ]
          —— 集里面属于tuple，用大括号
          
          —— 定义http中的每一个意义，“/”的意思“/home”页面：
          —— 写的手法和python很像，每个页面要做什么，先define再return：
          —— 连接html用return render_template('home.html', posts=posts)表示：连谁，什么要求。
          @app.route("/")
          @app.route("/home")
          def home():
              return render_template('home.html', posts=posts)

          @app.route("/about")
          def about ():
              return render_template('about.html',title="About Page")

          if __name__=="__main__":
              app.run(debug=True)


4) Templates～/ layout - inheritance - html

          Templates
          一般在python中，用templates装渲染用的html。
          在python中用render_template去引用html。注意，templates的级别
          这边的引用放在下面的格式里面
          {% if %}
          {% endif %}
          
          Inheritance
          长得一样的可以一起更改。省的改好多地方。写了一个layout.html来做总表：
          </head>
              CSS等
              下面说的是：如果有title，用它，没有，用第二个
              
              {% if title %}
                  <title>Flask Blog - {{ title }}</title>
              {% else %}
                  <title>Flask Blog</title>
              {% endif %}
          </head>
          
          唯一不同点是content部分，所以这一块放置一块区域：
          {% block content %}{% endblock %}
          
          home和about里面相似的都放在layout里面，
          用{% extends "layout.html" %}来inherited；
          
          —— home里面有文段，所以有post ——
          
                    {% extends "layout.html" %}
                    {% block content %}
                              {% for post in posts %}
                              。。。
                              。。。
                              {% endfor %}
                    {% endblock content %}
                    
          -— about没有post，所以只有标题 ——
          
                    {% extends "layout.html" %}
                    {% block content %}
                        <h1>About Page</h1>
                    {% endblock content%}


5) bootstrap - CSS & JS

          用来引用内置结构的，包括css,javascript。JS在楼下body最后一行。

          copy


？？？
1）我出现127.0.0.1可以访问，但是localhost不行！
去找hosts文件，去除：：1， 可是我没有权限。 用cmd+ctrl+G -> /hosts ->enter

##
# Host Database
#
# localhost is used to configure the loopback interface
# when the system is booting.  Do not change this entry.
##
127.0.0.1	localhost
255.255.255.255	broadcasthost
::1             localhost
