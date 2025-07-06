```
	@Composable  
	fun Verify(){  
	    val context = LocalContext.current  
	    val width = 265.dp  
	    val height = 70.dp  
	    Box(  
	        modifier = Modifier  
	            .fillMaxSize()  
	    ){  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomStart)  
	                .padding(bottom = 0.dp, start = 0.dp)  
	                .height(height)  
	                .width(width),  
	            shape = RoundedCornerShape(0.dp)  
	        ){  
	            Text(text="7", fontSize = 25.sp)  
	        }  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomCenter)  
	                .width(width)  
	                .height(height)  
	                .padding(bottom = 0.dp, start = 0.dp),  
	            shape = RoundedCornerShape(0.dp)  
	        ) {  
	            Text(text="8", fontSize = 25.sp)  
	        }  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomEnd)  
	                .width(width)  
	                .height(height)  
	                .padding(bottom = 0.dp, end = 0.dp),  
	            shape = RoundedCornerShape(0.dp)  
	        ) {  
	            Text(text="9", fontSize = 25.sp)  
	        }  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomStart)  
	                .padding(bottom = height, start = 0.dp)  
	                .width(width)  
	                .height(height),  
	            shape = RoundedCornerShape(0.dp)  
	        ) {  
	            Text(text="4", fontSize = 25.sp)  
	        }  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomCenter)  
	                .padding(bottom = height)  
	                .width(width)  
	                .height(height),  
	            shape = RoundedCornerShape(0.dp)  
	        ) {  
	            Text(text="5", fontSize = 25.sp)  
	        }  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomEnd)  
	                .padding(bottom = height, end = 0.dp)  
	                .width(width)  
	                .height(height),  
	            shape = RoundedCornerShape(0.dp)  
	        ) {  
	            Text(text="6", fontSize = 25.sp)  
	        }  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomEnd)  
	                .padding(bottom = height*2, end = 0.dp)  
	                .width(width)  
	                .height(height),  
	            shape = RoundedCornerShape(0.dp)  
	        ) {  
	            Text(text="3", fontSize = 25.sp)  
	        }  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomCenter)  
	                .padding(bottom = height*2)  
	                .width(width)  
	                .height(height),  
	            shape = RoundedCornerShape(0.dp)  
	        ) {  
	            Text(text="2", fontSize = 25.sp)  
	        }  
	        Button(  
	            onClick = {},  
	            modifier = Modifier  
	                .align(Alignment.BottomStart)  
	                .padding(bottom = height*2, start = 0.dp)  
	                .width(width)  
	                .height(height),  
	            shape = RoundedCornerShape(0.dp)  
	        ) {  
	            Text(text="1", fontSize = 25.sp)  
	        }  
	    }}
```
