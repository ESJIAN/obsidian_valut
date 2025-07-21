# 知乎回答
## 1. 一个最小的应用

flask教程都喜欢用一个非常小的应用示例向你展示flask的小巧灵活，例如下面的这个应用

```python
from flask import Flask
app = Flask(__name__)


@app.route('/')
def hello_world():
    return 'Hello World!'



if __name__ == '__main__':
    app.run(port=5678)
```

真正的flask应用，绝不可能是如此的短小，而是划分许多模块，要提供很多功能。

## 2. 一个稍大点的flask应用

下面的flask应用里，有一个user模块专门提供和用户有关的功能，例如用户注册，登录，登出，修改密码。还有一个admin模块，用来做后台管理，本示例只是为了向你展示如何在一个脚本里编写所有的模块，因此这些视图函数并没有具体的实现。

```python
from flask import Flask
app = Flask(__name__)


@app.route('/')
def hello_world():
    return 'Hello World!'


# user模块
@app.route('/user/register')
def register():
    return 'register'

@app.route('/user/login')
def login():
    return 'login'

@app.route('/user/modify_password')
def modify_password():
    return 'modify_password'


# admin模块
@app.route('/admin/alluser')
def alluser():
    return 'alluser'


@app.route('/admin/deluser')
def deluser():
    return 'deluser'



if __name__ == '__main__':
    app.run(port=5678)
```

和最小的flask应用相比，这个应用多了两个模块，5个视图函数，这仍然是一个非常小的flask应用。在实践项目中，子模块和视图函数会非常的多，因此，不可能将他们都写在同一个脚本里，那样的话，这个脚本会非常的大，难以维护。

## 3. BluePrint 蓝图技术

蓝图技术，可以帮助你实现flask应用的模块划分，对于没有亲身经历过大项目的人来说，很难理解模块划分的好处，换一种阐述方式，没有经历过大项目的人，根本不知道不划分模块或者模块划分不合理所带来的麻烦。

我将第2小节的应用划分出两个模块，划分后，项目结构不再是一个单一的脚本，一个模块拥有一个属于自己的文件目录，与之相关的代码都将写在这里，项目结构如下：

```text
blue-example/
├── admin
│   ├── __init__.py
│   └── views.py
├── app.py
└── user
    ├── __init__.py
    └── views.py
```

接下来，展示这些脚本里的内容

### 3.1 [app.py](https://link.zhihu.com/?target=http%3A//app.py/)

```python
from flask import Flask
app = Flask(__name__)


@app.route('/')
def hello_world():
    return 'Hello World!'



from admin import admin_blue
from user import user_blue

app.register_blueprint(admin_blue)
app.register_blueprint(user_blue)



if __name__ == '__main__':
    app.run(port=5678)
```

[app.py](https://link.zhihu.com/?target=http%3A//app.py/) 明显瘦身了，代码看起来干净整洁

### 3.2 user模块

**user/init.py**

```python
from flask import Blueprint

user_blue = Blueprint('user', __name__, url_prefix='/user')
from . import views
```

**user/views.py**

```python
from user import user_blue


# user模块
from user import user_blue


# user模块
@user_blue.route('/register')
def register():
    return 'register'

@user_blue.route('/login')
def login():
    return 'login'

@user_blue.route('/modify_password')
def modify_password():
    return 'modify_password'
```

### 3.3 admin

**admin/init.py**

```python
from flask import Blueprint


admin_blue = Blueprint('admin', __name__, url_prefix='/admin')
from . import views
```

**admin/views.py**

```python
from admin import admin_blue


# admin模块
@admin_blue.route('/alluser')
def alluser():
    return 'alluser'


@admin_blue.route('/deluser')
def deluser():
    return 'deluser'
```

第3小节的项目代码，多了一些模块的划分，自然也多了一些文件目录，而且咋看起来，比第2小节的代码变复杂了些，但这种“复杂”是值得的， 它换来了整个项目清晰的结构，很好的控制了单个脚本的代码规模。

## 4. 两种代码组织形式

蓝图在组织flask代码时，有两种形式

1. 功能式架构
2. 分区式架构

前面所展示的就是功能式架构，一个功能，一个模块组织成一个蓝图，他们共用相同的静态资源，静态资源放在static目录下，本文所举实例太简单，因此没有创建静态资源，功能式架构类似于下面的结构

```text
__init__.py
static/
templates/
    home/
    control_panel/
    admin/
views/
    __init__.py
    home.py
    control_panel.py
    admin.py
models.py
```

home, control_panel,admin 都是蓝图，他们共用static和 templates。

分区式架构，适用于子模块有特殊需要的情况，在创建蓝图构造Blueprint对象时，可以指定static和templates， 其结构类似于下面这样

```text
yourapp/
    __init__.py
    admin/
        __init__.py
        views.py
        static/
        templates/
    home/
        __init__.py
        views.py
        static/
        templates/
    control_panel/
        __init__.py
        views.py
        static/
        templates/
    models.py
```

试想，如果admin, home， control_panel有各自不同的页面样式和风格，那么他们就需要不同的静态资源，css, javascript,每个模块拥有各自的静态资源就是一个合理的选择。这样组织，还有一个好处，一个模块，或者说一个蓝图拥有自身全部的资源，包括static和templates，那么它可以很容易从一个项目里拆分出来放在另一个项目中使用。


# 官方手册
Flask 使用 _蓝图_ 的概念来制作应用程序组件并支持应用程序内或跨应用程序的通用模式。 蓝图可以极大地简化大型应用程序的工作方式，并为 Flask 扩展在应用程序上注册操作提供一个中心手段。 `Blueprint` 对象的工作方式与 `Flask` 应用程序对象类似，但它实际上不是应用程序。 相反，它是关于如何构建或扩展应用程序的 _蓝图_ 。

## 为什么是蓝图？

Flask 中的蓝图适用于以下情况：

- 将应用程序分解为一组蓝图。 这是大型应用的理想选择； 一个项目可以实例化一个应用程序对象，初始化几个扩展，并注册一组蓝图。
- 在 URL 前缀和/或子域的应用程序上注册蓝图。 URL 前缀/子域中的参数成为蓝图中所有视图函数的通用视图参数（具有默认值）。
- 在具有不同 URL 规则的应用程序上多次注册蓝图。
- 通过蓝图提供模板过滤器、静态文件、模板和其他实用程序。 蓝图不必实现应用程序或视图功能。
- 在初始化 Flask 扩展时，为任何这些情况在应用程序上注册蓝图。

Flask 中的蓝图不是可插拔的应用程序，因为它实际上不是一个应用程序——它是一组可以在应用程序上注册的操作，甚至可以多次注册。 为什么没有多个应用程序对象？ 您可以这样做（请参阅 [应用程序调度](https://cainiaojiaocheng.com/Flask/docs/2.0.x/patterns/appdispatch "Flask/docs/2.0.x/patterns/appdispatch") ），但您的应用程序将具有单独的配置，并将在 WSGI 层进行管理。

蓝图在 Flask 级别提供分离，共享应用程序配置，并且可以根据需要在注册时更改应用程序对象。 缺点是一旦创建了应用程序，您就无法取消注册蓝图，而不必销毁整个应用程序对象。

  

## 蓝图的概念

蓝图的基本概念是它们记录在应用程序上注册时要执行的操作。 Flask 在分派请求和生成从一个端点到另一个端点的 URL 时将视图函数与蓝图相关联。

  

## 创建蓝图

这就是一个非常基本的蓝图的样子。 在这种情况下，我们想要实现一个简单渲染静态模板的蓝图：

```python
from flask import Blueprint, render_template, abort
from jinja2 import TemplateNotFound
# 第一步：创建蓝图对象
simple_page = Blueprint('simple_page', __name__,
                        template_folder='templates')
# 蓝图名字——蓝图对象名——蓝图所在的py模块相互关联绑定
# 第二部：配置蓝图装饰容器并绑定函数
@simple_page.route('/', defaults={'page': 'index'})
@simple_page.route('/<page>')
def show(page):
    try:
        return render_template(f'pages/{page}.html')
    except TemplateNotFound:
        abort(404)
```


==当您在`@simple_page.route`装饰器的帮助下绑定一个函数时，蓝图会记录在应用程序上注册`show`函数的意图，以便稍后注册。 此外，它会在函数的端点前面加上蓝图的名称，该名称是给 `Blueprint` 构造函数（在本例中也是 `simple_page`）。 蓝图的名称不会修改 URL，只会修改端点。==

  

## 注册蓝图

那么如何注册那个蓝图呢？ 像这样：

```python
from flask import Flask
from yourapplication.simple_page import simple_page

app = Flask(__name__)
app.register_blueprint(simple_page) # 在app实例上注册蓝图
```



如果您检查应用程序上注册的规则，您会发现这些：

```python
>>> app.url_map
Map([<Rule '/static/<filename>' (HEAD, OPTIONS, GET) -> static>,
 <Rule '/<page>' (HEAD, OPTIONS, GET) -> simple_page.show>,
 <Rule '/' (HEAD, OPTIONS, GET) -> simple_page.show>])
```



第一个显然来自应用程序本身的静态文件。 另外两个是针对`simple_page`蓝图的show功能。 如您所见，它们也以蓝图名称为前缀，并以点分隔 (`.`)。

但是，蓝图也可以安装在不同的位置：

```python
app.register_blueprint(simple_page, url_prefix='/pages')
```

果然，这些是生成的规则：

```python
>>> app.url_map
Map([<Rule '/static/<filename>' (HEAD, OPTIONS, GET) -> static>,
 <Rule '/pages/<page>' (HEAD, OPTIONS, GET) -> simple_page.show>,
 <Rule '/pages/' (HEAD, OPTIONS, GET) -> simple_page.show>])
```

最重要的是，您可以多次注册蓝图，但并非每个蓝图都可以正确响应。 实际上，如果可以多次挂载，则取决于蓝图的实现方式。

  
## 小节总结
- ==创建==：创建子蓝图对象，将其关联到蓝图名字下，且蓝图对象所在的py程序也被关联到该蓝图名下，在创建父蓝图对象，将子蓝图对象关联到父蓝图对象
	-Tip：建议画好类似于下面fiinote所示的树状图来梳理关系
- ==注册==：先flask实例上注册父蓝图，所有子蓝图与父蓝图形成的蓝图关系树最后要能回到flask实例上
	-Tip：父蓝图注册子蓝图时候register_blueprint传入的是子蓝图的蓝图对象名字，所以还得导入子模块的蓝图对象 
- ==启动==：
- ==工作==：[fiilnote工作流](https://www.suishouxie.com/gpage.jsp?pi=qnves3f3fm2twtgrsvntwasjke)
	-子蓝图的uri地址与父uri是递进关系，详情见下面描述
## 嵌套蓝图

可以在另一个蓝图上注册一个蓝图。

```python
parent = Blueprint('parent', __name__, url_prefix='/parent')
child = Blueprint('child', __name__, url_prefix='/child')
parent.register_blueprint(child)# 把child蓝图注册到parent蓝图下
app.register_blueprint(parent) # 把parent蓝图注册到app下
```
==子蓝图将获得父名称作为其名称的前缀，子 URL 将以父 URL 前缀作为前缀。==

```python
url_for('parent.child.create')
/parent/child/create
```

特定于蓝图的前请求函数等。 与父母注册将触发孩子。 如果子级没有可以处理给定异常的错误处理程序，则将尝试父级的错误处理程序。

  

## 蓝图资源

蓝图也可以提供资源。 有时您可能只想为其提供的资源引入蓝图。

### 蓝图资源文件夹

与常规应用程序一样，蓝图被视为包含在文件夹中。 虽然多个蓝图可以来自同一个文件夹，但并非一定如此，通常不建议这样做。

该文件夹是从 `Blueprint` 的第二个参数推断出来的，通常是 __name__。 此参数指定与蓝图对应的逻辑 Python 模块或包。 如果它指向一个实际的 Python 包，该包（它是文件系统上的一个文件夹）就是资源文件夹。 如果是模块，则包含该模块的包将是资源文件夹。 您可以访问 `Blueprint.root_path` 属性以查看资源文件夹是什么：

```python
>>> simple_page.root_path
'/Users/username/TestProject/yourapplication'
```

Copy

要从此文件夹快速打开源代码，您可以使用 `open_resource()` 功能：

```python
with simple_page.open_resource('static/style.css') as f:
    code = f.read()
```

Copy

### 静态文件

蓝图可以通过使用 `static_folder` 参数提供文件系统上文件夹的路径来公开包含静态文件的文件夹。 它是绝对路径或相对于蓝图的位置：

```python
admin = Blueprint('admin', __name__, static_folder='static')
```

Copy

默认情况下，路径的最右边部分是它在 Web 上公开的位置。 这可以通过 `static_url_path` 参数进行更改。 因为文件夹在这里被称为`static`，它会在蓝图的`url_prefix`+`/static`处可用。 如果蓝图具有前缀 `/admin`，则静态 URL 将为 `/admin/static`。

端点名为 `blueprint_name.static`。 您可以使用 `url_for()` 生成指向它的 URL，就像使用应用程序的静态文件夹一样：

```python
url_for('admin.static', filename='style.css')
```

Copy

但是，如果蓝图没有 `url_prefix`，则无法访问蓝图的静态文件夹。 这是因为在这种情况下 URL 将是 `/static`，并且应用程序的 `/static` 路由优先。 与模板文件夹不同，如果应用程序静态文件夹中不存在该文件，则不会搜索蓝图静态文件夹。

  

### 模板

如果您希望蓝图公开模板，您可以通过向 `Blueprint` 构造函数提供 template_folder 参数来实现：

```python
admin = Blueprint('admin', __name__, template_folder='templates')
```

Copy

对于静态文件，路径可以是相对于蓝图资源文件夹的绝对路径或相对路径。

模板文件夹被添加到模板的搜索路径中，但其优先级低于实际应用程序的模板文件夹。 这样您就可以轻松地覆盖蓝图在实际应用程序中提供的模板。 这也意味着如果您不希望蓝图模板被意外覆盖，请确保没有其他蓝图或实际应用程序模板具有相同的相对路径。 当多个蓝图提供相同的相对模板路径时，注册的第一个蓝图优先于其他蓝图。

因此，如果您在文件夹 `yourapplication/admin` 中有蓝图并且想要渲染模板 `'admin/index.html'` 并且您提供 `templates` 作为 template_folder，您将拥有创建这样的文件：`yourapplication/admin/templates/admin/index.html`。 额外的 `admin` 文件夹的原因是为了避免我们的模板被实际应用程序模板文件夹中名为 `index.html` 的模板覆盖。

为了进一步重申这一点：如果您有一个名为 `admin` 的蓝图，并且您想要渲染一个特定于该蓝图的名为 `index.html` 的模板，最好的方法是这样布置您的模板：

```python
yourpackage/
    blueprints/
        admin/
            templates/
                admin/
                    index.html
            __init__.py
```

Copy

然后当你想渲染模板时，使用 `admin/index.html` 作为名称来查找模板。 如果您在加载正确模板时遇到问题，请启用 `EXPLAIN_TEMPLATE_LOADING` 配置变量，该变量将指示 Flask 打印出它在每个 `render_template` 调用上定位模板所经历的步骤。

  

## 构建 URL

如果你想从一个页面链接到另一个页面，你可以像往常一样使用 `url_for()` 函数，只需在 URL 端点前面加上蓝图的名称和一个点 (`.` )：

```python
url_for('admin.index')
```

Copy

此外，如果您在蓝图或渲染模板的视图函数中，并且想要链接到同一蓝图的另一个端点，则可以通过仅在端点前添加一个点来使用相对重定向：

```python
url_for('.index')
```

Copy

例如，这将链接到 `admin.index`，以防当前请求被分派到任何其他管理蓝图端点。

  

## 蓝图错误处理程序

蓝图像 `Flask` 应用程序对象一样支持 `errorhandler` 装饰器，因此很容易制作特定于蓝图的自定义错误页面。

以下是“404 页面未找到”异常的示例：

```python
@simple_page.errorhandler(404)
def page_not_found(e):
    return render_template('pages/404.html')
```

Copy

大多数错误处理程序会按预期工作； 但是，有一个关于 404 和 405 异常处理程序的警告。 这些错误处理程序只能从适当的 `raise` 语句或另一个蓝图视图函数中对 `abort` 的调用中调用； 例如，它们不会被无效的 URL 访问调用。 这是因为蓝图并不“拥有”某个 URL 空间，因此如果给定无效 URL，应用程序实例无法知道它应该运行哪个蓝图错误处理程序。 如果您想根据 URL 前缀对这些错误执行不同的处理策略，可以使用 `request` 代理对象在应用程序级别定义它们：

```python
@app.errorhandler(404)
@app.errorhandler(405)
def _handle_api_error(ex):
    if request.path.startswith('/api/'):
        return jsonify(error=str(ex)), ex.code
    else:
        return ex
```

Copy

请参阅 [处理应用程序错误](https://cainiaojiaocheng.com/Flask/docs/2.0.x/errorhandling "Flask/docs/2.0.x/errorhandling") 。


# 总结：
