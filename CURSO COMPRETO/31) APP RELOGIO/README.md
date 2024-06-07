# APP RELOGIO
Para criar um aplicativo de relógio básico no Android, você pode seguir estas etapas:

## 1. Layout XML:
Crie um layout XML para exibir o relógio na interface do usuário. Aqui está um exemplo simples usando um TextView:

```xml
<!-- activity_main.xml -->
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center">

    <TextView
        android:id="@+id/textClock"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="40sp"
        android:textColor="#000000"
        android:text="00:00:00"
        android:layout_centerInParent="true"/>

</RelativeLayout>
```

## 2. Lógica da Activity:
Implemente a lógica na Activity para atualizar o TextView com a hora atual.

```kotlin
// MainActivity.kt
package com.example.clockapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.Handler
import android.os.Looper
import android.widget.TextView
import java.text.SimpleDateFormat
import java.util.*

class MainActivity : AppCompatActivity() {

    private lateinit var textClock: TextView
    private val dateFormat = SimpleDateFormat("HH:mm:ss", Locale.getDefault())
    private val handler = Handler(Looper.getMainLooper())

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        textClock = findViewById(R.id.textClock)

        // Atualiza o relógio a cada segundo
        handler.post(object : Runnable {
            override fun run() {
                updateClock()
                handler.postDelayed(this, 1000)
            }
        })
    }

    private fun updateClock() {
        val currentTime = dateFormat.format(Date())
        textClock.text = currentTime
    }

    override fun onDestroy() {
        super.onDestroy()
        // Para de atualizar o relógio quando a Activity é destruída
        handler.removeCallbacksAndMessages(null)
    }
}
```

## 3. Executar o Aplicativo:
Compile e execute o aplicativo no dispositivo ou emulador Android. O TextView deve exibir a hora atual e atualizar a cada segundo.

Este é um exemplo básico de como criar um aplicativo de relógio simples no Android. Você pode personalizá-lo conforme necessário, adicionando mais recursos, como formatos de hora personalizados, alarmes, cronômetros, etc.