从网页跳转微信得到启发，网页链接weixin://就可以打开微信，那么如果要自己写一个app然后在网页打开呢？
询问chatgpt得知这是因为微信设置了自己的url scheme，那么我们可以在自己的代码里设置scheme，下面以安卓开发jetpack compose，kotlin语言为例，在AndroidManifest.xml文件中添加：
```
<activity android:name=".MainActivity">
    <intent-filter>
        <action android:name="android.intent.action.VIEW"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <category android:name="android.intent.category.BROWSABLE"/>
        <data android:scheme="myapp"/> <!-- 这里的 "myapp" 就是你的 URL Scheme -->
    </intent-filter>
</activity>

```
这样在网页中跳转链接到"myapp://......"就可以打开你的app了

在app中如此获取参数：
```
class MainActivity : ComponentActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
        /**setContent {  
            IntentTestTheme {                Main(path, query)            }        }**/        val intent = intent  
        val data: Uri? = intent.data  
  
        if (data != null && "intenttest" == data.scheme){  
            val path = data.path  
            val query = data.query  
            setContent{  
                IntentTestTheme {  
                    Main(path, query)  
                }  
            }        }else{  
            setContent{  
                Main("noPath", "noQuery")  
            }  
        }  
    }  
}
```
