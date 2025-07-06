```
@Composable  
fun BasicLazyColumn() {  
    // 假设我们有一个字符串列表作为数据源  
    val items = remember { mutableStateListOf<String>() }  
  
    for (i in 1..10){  
        items.add(i.toString())  
    }  
    LaunchedEffect(true) {  
        delay(1000)  
        items.add("11")  
    }  
    LazyColumn(  
        modifier = Modifier  
            .padding(16.dp) // 为列表添加一些内边距  
    ) {  
        items(items) { item ->  
            // 对于列表中的每个项目，我们调用一个lambda来渲染它  
            Text(  
                text = item,  
                fontSize = 18.sp,  
                modifier = Modifier.padding(8.dp) // 为每个列表项添加一些内边距  
            )  
        }  
    }}
```
