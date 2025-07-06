```
@Composable
fun main(){
	val context = LocalContext.current
	 context.startActivity(context, MainActivity2::class.java)
	 //不传参
	 context.startActivity(context, MainActivity2::class.java).apply{
		 putExtra("name", value)
	 }//传参
	 
}

//接收参数
setContent {  
		val phone = intent.getStringExtra("phone") 
}

//返回activity

(context as? Activity)?.finish()
```
