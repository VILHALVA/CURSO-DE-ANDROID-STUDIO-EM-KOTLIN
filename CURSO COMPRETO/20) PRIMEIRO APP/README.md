# PRIMEIRO APP
Começar com um clássico como o "Olá Mundo" é uma excelente ideia para aprender o básico do desenvolvimento de aplicativos Android. Vamos começar criando um novo projeto no Android Studio e então eu fornecerei os trechos de código necessários.

## Criando o Projeto no Android Studio:
1. Abra o Android Studio.
2. Selecione "Create New Project" no menu inicial.
3. Escolha "Empty Activity" e clique em "Next".
4. Dê um nome ao seu projeto, por exemplo, "OlaMundoApp", e clique em "Finish".

Agora que o projeto está criado, vamos adicionar o código necessário.

## Trecho de Código Kotlin (MainActivity.kt):
Este será o código responsável por exibir a mensagem "Olá Mundo!" na tela quando o aplicativo for iniciado.

```kotlin
package com.example.olamundoapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.TextView

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Referenciar o TextView
        val textView: TextView = findViewById(R.id.textView)

        // Definir o texto do TextView como "Olá Mundo!"
        textView.text = "Olá Mundo!"
    }
}
```

## Trecho de Código XML (activity_main.xml):
Este arquivo XML define a estrutura da interface do usuário (UI) da nossa atividade principal, onde exibiremos a mensagem "Olá Mundo!".

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="TextView"
        android:layout_centerInParent="true"
        android:textSize="24sp" />

</RelativeLayout>
```

## Caminho do Diretório:
- **MainActivity.kt**: `app/src/main/java/com/example/olamundoapp/MainActivity.kt`
- **activity_main.xml**: `app/src/main/res/layout/activity_main.xml`

Certifique-se de substituir `com.example.olamundoapp` pelo nome do pacote que você definiu ao criar o projeto. Após adicionar esses trechos de código aos arquivos correspondentes, você pode executar o aplicativo no emulador ou em um dispositivo Android e ver a mensagem "Olá Mundo!" sendo exibida na tela.