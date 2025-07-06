权限
```
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />  
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"  
    android:maxSdkVersion="28" /> <!-- 仅适用于 Android 9 及以下 -->
```

函数
```
//写入
fun writeToFile(context: Context, fileName: String, data: String) {  
    try {  
        val outputStream: FileOutputStream = context.openFileOutput(fileName, Context.MODE_PRIVATE)  
        outputStream.write(data.toByteArray())  
        outputStream.close()  
    } catch (e: Exception) {  
        e.printStackTrace()  
    }  
}
```

```
//读取
fun readFromFile(context: Context, fileName: String): String {  
    return try {  
        val inputStream: FileInputStream = context.openFileInput(fileName)  
        val content = inputStream.bufferedReader().use { it.readText() }  
        inputStream.close()  
        content  
    } catch (e: Exception) {  
        e.printStackTrace()  
        ""  
    }  
}
```
