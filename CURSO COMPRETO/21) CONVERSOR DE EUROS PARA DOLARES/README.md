# CONVERSOR DE EUROS PARA DOLARES
Vamos criar um aplicativo simples que converta o valor em euros para dólares. Aqui estão os trechos de código Kotlin e XML que você precisa para criar esse aplicativo.

## Criando o Projeto no Android Studio:
1. Abra o Android Studio.
2. Selecione "Create New Project" no menu inicial.
3. Escolha "Empty Activity" e clique em "Next".
4. Dê um nome ao seu projeto, por exemplo, "ConversorMoeda", e clique em "Finish".

Agora, vamos adicionar os trechos de código necessários.

## Trecho de Código Kotlin (MainActivity.kt):
Este código será responsável por realizar a conversão de euros para dólares.

```kotlin
package com.example.conversormoeda

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val etEuros: EditText = findViewById(R.id.etEuros)
        val btnConverter: Button = findViewById(R.id.btnConverter)
        val tvResultado: TextView = findViewById(R.id.tvResultado)

        btnConverter.setOnClickListener {
            val euros = etEuros.text.toString().toDouble()
            val taxaConversao = 1.18 // Taxa de conversão de euros para dólares
            val dolares = euros * taxaConversao
            tvResultado.text = "$euros euros são ${String.format("%.2f", dolares)} dólares."
        }
    }
}
```

## Trecho de Código XML (activity_main.xml):
Este arquivo XML define a interface do usuário (UI) da nossa atividade principal, com um EditText para o usuário inserir o valor em euros, um Button para iniciar a conversão e um TextView para exibir o resultado em dólares.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/etEuros"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Insira o valor em euros"
        android:inputType="numberDecimal"
        android:layout_margin="16dp" />

    <Button
        android:id="@+id/btnConverter"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Converter"
        android:layout_below="@id/etEuros"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp" />

    <TextView
        android:id="@+id/tvResultado"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text=""
        android:textSize="20sp"
        android:layout_below="@id/btnConverter"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp" />

</RelativeLayout>
```

## Caminho do Diretório:
- **MainActivity.kt**: `app/src/main/java/com/example/conversormoeda/MainActivity.kt`
- **activity_main.xml**: `app/src/main/res/layout/activity_main.xml`

Após adicionar esses trechos de código aos arquivos correspondentes, você pode executar o aplicativo no emulador ou em um dispositivo Android e testar a conversão de euros para dólares.