```
package com.wjwcj.objectrec  
  
import android.content.Intent  
import android.net.Uri  
import android.os.Bundle  
import android.provider.MediaStore  
import android.util.Log  
import android.widget.Toast  
import androidx.activity.ComponentActivity  
import androidx.activity.compose.rememberLauncherForActivityResult  
import androidx.activity.compose.setContent  
import androidx.activity.enableEdgeToEdge  
import androidx.activity.result.ActivityResultLauncher  
import androidx.activity.result.PickVisualMediaRequest  
import androidx.activity.result.contract.ActivityResultContracts  
import androidx.compose.foundation.Image  
import androidx.compose.foundation.layout.fillMaxSize  
import androidx.compose.foundation.layout.padding  
import androidx.compose.material3.Scaffold  
import androidx.compose.material3.Text  
import androidx.compose.runtime.Composable  
import androidx.compose.runtime.LaunchedEffect  
import androidx.compose.ui.Modifier  
import androidx.compose.ui.platform.LocalContext  
import androidx.compose.ui.tooling.preview.Preview  
import androidx.core.app.ActivityCompat.startActivityForResult  
import com.wjwcj.objectrec.ui.theme.ObjectRecTheme  
import java.net.URI  
  
class MainActivity : ComponentActivity() {  
    var ImageUri:Uri? = null  
    override fun onCreate(savedInstanceState: Bundle?) {  
        super.onCreate(savedInstanceState)  
        enableEdgeToEdge()  
        // Registers a photo picker activity launcher in single-select mode.  
        val pickMedia = registerForActivityResult(ActivityResultContracts.PickVisualMedia()) { uri ->  
            // Callback is invoked after the user selects a media item or closes the  
            // photo picker.            ImageUri = uri  
            if (uri != null) {  
                Log.d("PhotoPicker", "Selected URI: $uri")  
            } else {  
                Log.d("PhotoPicker", "No media selected")  
            }  
        }  
  
        setContent {  
            Greeting(  
                pickMedia = pickMedia,  
                uri = ImageUri  
            )  
        }  
  
  
    }  
}  
  
  
  
  
  
  
@Composable  
fun Greeting(pickMedia: ActivityResultLauncher<PickVisualMediaRequest>, uri: Uri?) {  
    Thread.sleep(3000)  
    val context = LocalContext.current  
    Toast.makeText(context, uri.toString(), Toast.LENGTH_SHORT).show()  
    // Launch the photo picker and let the user choose images and videos.  
    pickMedia.launch(PickVisualMediaRequest(ActivityResultContracts.PickVisualMedia.ImageAndVideo))  
  
}
```