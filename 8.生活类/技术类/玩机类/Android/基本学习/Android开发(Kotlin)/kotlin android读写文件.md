```
//因为是内部储存所以无需请求储存权限

fun writeFile(context: Context, filename: String, content: String) {  
    try {  
        val file = File(context.filesDir, filename)  
        file.writeText(content)  
    } catch (e: IOException) {  
        e.printStackTrace()  
    }  
}  
  
fun readFile(context: Context, filename: String): String? {  
    try {  
        val file = File(context.filesDir, filename)  
        return file.readText(Charsets.UTF_8)  
    } catch (e: IOException) {  
        e.printStackTrace()  
    }  
    return null  
}
```
