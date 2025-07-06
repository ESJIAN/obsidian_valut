![](https://i-blog.csdnimg.cn/blog_migrate/0d4de63cbbb5e71f5f836a57a5ec91b0.png)

 1. 屏幕坐标系：以屏幕的左上角为原点，如图所示  
GetWindowRect() 函数获得的 [RECT](https://so.csdn.net/so/search?q=RECT&spm=1001.2101.3001.7020) 就是以屏幕坐标系算的。

2. 非客户区坐标系(窗口坐标系)  
包括标题栏的部分。GetWindowDC 返回的设备环境就是基于此坐标系，一般只在 WM_NCPAINT 消息中使用。

3. 客户区坐标系  
不包括标题栏，坐标的原点在标题栏下的客户区的左上角。  
BeginPaint 函数返回的设备环境是基于客户区坐标系的，只在 WM_PAINT 消息中使用，与 EndPaint 函数成对使用。  
GetDC 函数返回的设备环境也是基于客户区坐标系的，可以在其他消息中使用，与 ReleaseDC 函数成对使用。  
GetClientRect 函数获得的RECT 是基于客户区坐标系的，RECT 的左上角坐标一定是(0,0)。

ScreenToClient 函数将 屏幕坐标系的坐标 --> 客户区坐标系的坐标  
ClientToScreen 函数将 客户区坐标系的坐标 --> 屏幕坐标系的坐标

MoveWindow 函数，移动的是主窗口时传入的 RECT 是基于屏幕坐标系的，若是移动的子窗口，基于的是父窗口的客户区坐标坐标系。