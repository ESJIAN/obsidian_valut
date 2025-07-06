```
fun EncodeBase64(data: String): String{
	// 将字符串转换为字节数组
	val dataBytes = data.toByteArray(Charsets.UTF_8)
	
	// 进行Base64编码
	val encodedBytes = Base64.encode(dataBytes, Base64.NO_WRAP)
	
	// 将编码后的字节数组转换为字符串
	val encodedString = String(encodedBytes, Charsets.UTF_8)
	return encodedString
}
```


普通kotlin
```
import java.util.Base64  
  
fun EncodeBase64(data:String):String{  
    val dataBytes = data.toByteArray(Charsets.UTF_8)  
    val encoder = Base64.getEncoder()  
    val encodedBytes = encoder.encode(dataBytes)  
    val encodedString = String(encodedBytes, Charsets.UTF_8)  
    return encodedString  
}
```
