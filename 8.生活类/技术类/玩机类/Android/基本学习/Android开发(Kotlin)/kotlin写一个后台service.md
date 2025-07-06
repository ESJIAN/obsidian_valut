
> 参考https://cloud.tencent.com/developer/ask/2120306/answer/2864586

创建一个kt文件单独放service(建议这么做)
新建一个类继承Service类
```  
class backWriteService: Service() {  
    @Nullable  
    override fun onBind(intent: Intent): IBinder?{  
        return null  
    }  
  
    override fun onStartCommand(intent: Intent?, flags: Int, startId: Int): Int {  
        GlobalScope.launch {  
            withContext(Dispatchers.IO){  
                var n = 0  
                while (true){  
                    try {  
                        writeFile(this@backWriteService, "test.txt", n.toString())  
                        n += 1  
                        Thread.sleep(1000)  
                    }  
                    catch (e: Exception){  
                        Thread.sleep(1000)  
                    }  
                }  
            }  
        }        return START_STICKY  
    }  
  
    override fun onDestroy() {  
        super.onDestroy()  
    }  
}
```

在AndroidManifest.xml中注册service

```
<service android:name=".backWriteService" />
```

在MainActivity中启动service:

```
val intent = Intent(this, backWriteService::class.java)  
this.startService(intent)
```

这个this如果是在compose中应当替换为context
在backWriteService类中那个this标记了一个@backWriteService
或者可以在onStartCommand开始的时候创建val context = this然后用这个context代替
注意相应的权限即完事儿~