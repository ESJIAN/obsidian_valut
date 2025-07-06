```
fun writeToFile(BytesData: ByteArray?, filePath:String) {  
    try{  
        if (BytesData != null) {  
            val file = File(filePath)  
            val outputStream: OutputStream = FileOutputStream(file)  
            outputStream.write(BytesData)  
            outputStream.flush()  
            outputStream.close()  
        }  
    }catch (e:Exception){  
        e.printStackTrace()  
    }  
}
```
