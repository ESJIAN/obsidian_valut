```
import java.io.IOException  
import java.io.InputStream  
import java.net.HttpURLConnection  
import java.net.URL  
import javax.net.ssl.HttpsURLConnection  
  
// 请求并返回响应内容  
fun get(url: String):InputStream?{  
    return try {  
		    //注意，安卓9.0以上是默认禁止使用http请求的(用https)，问问ai应该如何允许http
        val urlObject = URL(url)  
        val connection = urlObject.openConnection() as HttpURLConnection  
  
        // 如果是 https 请求，确保其类型是 HttpsURLConnection        
        if (connection is HttpsURLConnection) {  
            // 配置 SSL 证书（可选，取决于是否需要验证证书）  
            connection.sslSocketFactory  
        }  
  
        connection.requestMethod = "GET"  
        connection.readTimeout = 15000  
        connection.connectTimeout = 15000  
  
        // 获取响应代码并处理  
        when (connection.responseCode) {  
            HttpURLConnection.HTTP_OK -> {  
                // 读取响应内容  
//                BufferedReader(InputStreamReader(connection.inputStream)).use { reader ->  
//                    reader.readText()  
//                }  
                connection.inputStream  
                /**  
                 * 这样就可以在函数外处理inputStream **/  
            }  
            HttpURLConnection.HTTP_BAD_REQUEST -> {  
                null  
            }  
            HttpURLConnection.HTTP_UNAUTHORIZED -> {  
                null  
            }  
            HttpURLConnection.HTTP_FORBIDDEN -> {  
                null  
            }  
            HttpURLConnection.HTTP_NOT_FOUND -> {  
                null  
            }  
            HttpURLConnection.HTTP_INTERNAL_ERROR -> {  
                null  
            }  
            else -> {  
                null  
            }  
        }  
    } catch (e: IOException) {  
        null  
    } catch (e: Exception) {  
        null  
    }  
}
```
