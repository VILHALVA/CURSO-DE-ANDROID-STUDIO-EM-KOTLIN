# FORMULARIO NOME E SOBRENOME
Vamos criar um formulário simples para coletar o nome e sobrenome do usuário. Aqui estão os trechos de código Kotlin e XML necessários para isso:

## Criando o Projeto no Android Studio:
1. Abra o Android Studio.
2. Selecione "Create New Project" no menu inicial.
3. Escolha "Empty Activity" e clique em "Next".
4. Dê um nome ao seu projeto, por exemplo, "FormularioNomeSobrenome", e clique em "Finish".

Agora, vamos adicionar os trechos de código necessários.

## Trecho de Código Kotlin (MainActivity.kt):
Este código será responsável por capturar os valores inseridos pelo usuário e exibi-los em um TextView.

```kotlin
package com.example.formularionomesobrenome

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val etNome: EditText = findViewById(R.id.etNome)
        val etSobrenome: EditText = findViewById(R.id.etSobrenome)
        val btnEnviar: Button = findViewById(R.id.btnEnviar)
        val tvResultado: TextView = findViewById(R.id.tvResultado)

        btnEnviar.setOnClickListener {
            val nome = etNome.text.toString()
            val sobrenome = etSobrenome.text.toString()
            val nomeCompleto = "$nome $sobrenome"
            tvResultado.text = "Nome completo: $nomeCompleto"
        }
    }
}
```

## Trecho de Código XML (activity_main.xml):
Este arquivo XML define a interface do usuário (UI) da nossa atividade principal, com dois EditTexts para o usuário inserir o nome e sobrenome, um Button para enviar o formulário e um TextView para exibir o nome completo.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/etNome"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nome"
        android:layout_margin="16dp" />

    <EditText
        android:id="@+id/etSobrenome"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Sobrenome"
        android:layout_below="@id/etNome"
        android:layout_margin="16dp" />

    <Button
        android:id="@+id/btnEnviar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Enviar"
        android:layout_below="@id/etSobrenome"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp" />

    <TextView
        android:id="@+id/tvResultado"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text=""
        android:textSize="20sp"
        android:layout_below="@id/btnEnviar"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp" />

</RelativeLayout>
```

## Caminho do Diretório:
- **MainActivity.kt**: `app/src/main/java/com/example/formularionomesobrenome/MainActivity.kt`
- **activity_main.xml**: `app/src/main/res/layout/activity_main.xml`

Após adicionar esses trechos de código aos arquivos correspondentes, você pode executar o aplicativo no emulador ou em um dispositivo Android e testar o preenchimento do formulário. O nome completo inserido pelo usuário será exibido quando o botão "Enviar" for clicado.