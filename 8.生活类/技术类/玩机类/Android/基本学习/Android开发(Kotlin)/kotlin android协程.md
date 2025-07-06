```
suspend fun testApi():String{  
    return withContext(Dispatchers.IO) {  
        var a = 0  
        if (a - 1 > 0){  
            "yes"  
        }else{  
            "no"  
        }  
    }  
}



Button(onClick = {  
      GlobalScope.launch(Dispatchers.IO){  
        val result = testApi()  
        withContext(Dispatchers.Main){  
            Toast.makeText(context, result, Toast.LENGTH_SHORT).show()  
	    } 
	    } 
	}
```

