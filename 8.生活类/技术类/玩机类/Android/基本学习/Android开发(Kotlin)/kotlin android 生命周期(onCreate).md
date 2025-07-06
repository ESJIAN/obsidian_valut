`onCreate()` 和 `onDestroy()` 是 `Activity` 生命周期的一部分。完整的生命周期如下：

1. **`onCreate()`**：`Activity` 创建时调用。
    
2. **`onStart()`**：`Activity` 可见时调用。
    
3. **`onResume()`**：`Activity` 进入前台时调用。
    
4. **`onPause()`**：`Activity` 失去焦点时调用。
    
5. **`onStop()`**：`Activity` 不可见时调用。
    
6. **`onDestroy()`**：`Activity` 被销毁时调用。

### **`super` 关键字**

- **`super`** 是 Java 和 Kotlin 中的关键字，用于调用父类的方法或构造函数。
    
- 在 Android 中，`Activity` 或 `AppCompatActivity` 是当前类的父类，`super.onCreate()` 就是调用父类的 `onCreate()` 方法。

```
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        println("onCreate")
    }

    override fun onStart() {
        super.onStart()
        println("onStart")
    }

    override fun onResume() {
        super.onResume()
        println("onResume")
    }

    override fun onPause() {
        super.onPause()
        println("onPause")
    }

    override fun onStop() {
        super.onStop()
        println("onStop")
    }

    override fun onDestroy() {
        super.onDestroy()
        println("onDestroy")
    }

    override fun onRestart() {
        super.onRestart()
        println("onRestart")
    }
}
```