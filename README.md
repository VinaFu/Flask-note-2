# Flask-note-2

1) HTTP

          http://127.0.0.1:5000
          意义：整个为本地IP.127.0.0.1= local machine， localhost；5000 = 本地portal

          On most machines localhost and 127.0.0.1 are functionally identical. But localhost is a label for the IP address and not the address itself. Localhost could be pointed at different IP addresses.
          
2)DEBUG模式+get and 404/200

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
          
3）Templates

一般在python中，用templates装渲染用的html。
在python中用render_template去引用html。注意，templates
{%%}
{%end %}

4) layout




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
