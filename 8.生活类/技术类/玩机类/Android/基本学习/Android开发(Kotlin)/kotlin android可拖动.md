```
@Composable  
fun DraggableButtonExample() {  
    val context = LocalContext.current  
    // 使用 remember 来存储按钮的偏移位置  
    var offsetX by remember { mutableFloatStateOf(0f) }  
    var offsetY by remember { mutableFloatStateOf(0f) }  
  
    Box(  
        modifier = Modifier  
            .fillMaxSize()  
            .background(Color.LightGray),  
        contentAlignment = Alignment.Center  
    ) {  
        // 创建一个可拖动的按钮  
        Box(  
            modifier = Modifier  
                .offset { IntOffset(offsetX.roundToInt(), offsetY.roundToInt()) }  
                .size(80.dp)  
                .background(Color.Blue, shape = CircleShape)  
                .pointerInput(Unit) {  
                    // 检测拖动手势  
                    detectDragGestures (  
                        onDragEnd = {  
                            Toast.makeText(context, "放开了", Toast.LENGTH_SHORT).show()  
                        },  
                        onDragStart = {  
                            Toast.makeText(context, "开始拖动", Toast.LENGTH_SHORT).show()  
                        }  
  
                    ){ change, dragAmount ->  
                        // 消耗位置变化，表示我们处理了这个事件  
                        change.consume()  
                        // 更新偏移量  
                        offsetX += dragAmount.x  
                        offsetY += dragAmount.y  
                    }  
                },  
            contentAlignment = Alignment.Center  
        ) {  
            Text(  
                text = "可拖动",  
                color = Color.White,  
                style = MaterialTheme.typography.bodySmall  
            )  
        }  
    }}
    
```
