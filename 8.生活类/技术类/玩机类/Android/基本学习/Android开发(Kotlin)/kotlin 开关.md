```
@Composable  
fun SwitchScreen() {  
    var isSwitchOn by remember { mutableStateOf(false) }  
    var backColor by remember { mutableStateOf(Color(0xFFF6F6F6)) }  
    LaunchedEffect(isSwitchOn) {  
        if (isSwitchOn){  
            backColor = Color(0xFFF6F6F6)  
        }else{  
            backColor = Color(0xff000000)  
        }  
    }  
    Box(  
        modifier = Modifier  
            .fillMaxSize()  
            .background(backColor), // 设置背景色  
        contentAlignment = Alignment.Center  
    ) {  
        Column(  
            horizontalAlignment = Alignment.CenterHorizontally,  
            modifier = Modifier  
                .padding(16.dp)  
                .background(Color.White, shape = MaterialTheme.shapes.medium) // 白色卡片背景  
                .padding(24.dp) // 内部间距  
        ) {  
            Text(  
                text = "控制开关",  
                fontSize = 24.sp,  
                fontWeight = FontWeight.Bold,  
                color = Color(0xFF333333)  
            )  
  
            Spacer(modifier = Modifier.height(16.dp))  
  
            // 开关组件  
            Switch(  
                checked = isSwitchOn,  
                onCheckedChange = { isChecked ->  
                    isSwitchOn = isChecked  
                },  
                colors = SwitchDefaults.colors(  
                    checkedThumbColor = Color(0xFF4CAF50), // 开启时的颜色  
                    uncheckedThumbColor = Color(0xFFFF5722) // 关闭时的颜色  
                )  
            )  
  
            Spacer(modifier = Modifier.height(16.dp))  
  
            // 显示开关状态  
            Text(  
                text = if (isSwitchOn) "开关状态：开启" else "开关状态：关闭",  
                fontSize = 16.sp,  
                color = if (isSwitchOn) Color(0xFF4CAF50) else Color(0xFFFF5722),  
                fontWeight = FontWeight.Medium  
            )  
        }  
    }}
```
