```
class MainActivity : ComponentActivity() {  
    override fun onCreate(savedInstanceState: Bundle?) {  
  
        // 请求通知权限的注册器  
        val requestPermissionLauncher = registerForActivityResult(  
            ActivityResultContracts.RequestPermission()  
        ) { isGranted: Boolean ->  
            if (isGranted) {  
                sendNotification(this)  // 若已授权，则发送通知  
            } else {  
                // 权限被拒绝，您可以在此提示用户或执行相应逻辑  
            }  
        }  
        if (ContextCompat.checkSelfPermission(this, Manifest.permission.POST_NOTIFICATIONS)  
            == PackageManager.PERMISSION_GRANTED  
        ) {  
            // 已授权，直接发送通知  
            //sendNotification(this)  
        } else {  
            // 请求通知权限  
            requestPermissionLauncher.launch(Manifest.permission.POST_NOTIFICATIONS)  
        }  
  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
        setContent {  
            MayuanTheme {  
                ......
            }  
        }   
     }  
}

  
fun sendNotification(context: Context) {  
    val channelId = "my_channel_id"  
    val notificationId = 1  
  
    // 创建通知渠道 (仅适用于 Android 8.0+)    
    val channelName = "马原答案"  
    val importance = NotificationManager.IMPORTANCE_DEFAULT  
    val channel = NotificationChannel(channelId, channelName, importance).apply {  
        description = "发送马原答案的通知"  
    }  
  
    // 注册通知渠道  
    val notificationManager: NotificationManager =  
        context.getSystemService(Context.NOTIFICATION_SERVICE) as NotificationManager  
    notificationManager.createNotificationChannel(channel)  
  
  
    // 创建通知  
    val builder = NotificationCompat.Builder(context, channelId)  
        .setContentTitle("答案")  
        .setContentText("ABCD")  
        .setSmallIcon(R.drawable.ic_launcher_foreground)  //图标必填
        .setPriority(NotificationCompat.PRIORITY_DEFAULT)  
  
    // 显示通知  
    with(NotificationManagerCompat.from(context)) {  
        if (ActivityCompat.checkSelfPermission(  
                context,  
                Manifest.permission.POST_NOTIFICATIONS  
            ) != PackageManager.PERMISSION_GRANTED  
        ) {  
            return  
        }  
        notify(notificationId, builder.build())  
    }  
}
```

