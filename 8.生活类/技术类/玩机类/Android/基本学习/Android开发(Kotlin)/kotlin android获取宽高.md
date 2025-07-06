```
import android.content.Context
import android.util.DisplayMetrics

fun getMaxDpDimensions(context: Context): Pair<Float, Float> {
    val metrics = DisplayMetrics()
    context.display?.getMetrics(metrics) // 在API 30及以上版本中
    val widthPx = metrics.widthPixels
    val heightPx = metrics.heightPixels
    val density = metrics.density

    // 转换为dp
    val widthDp = widthPx / density
    val heightDp = heightPx / density

    return Pair(widthDp, heightDp)
}

// 在你的Activity或Fragment中调用
val (maxWidthDp, maxHeightDp) = getMaxDpDimensions(context)
println("最大可用宽度: $maxWidthDp dp")
println("最大可用高度: $maxHeightDp dp")
```
