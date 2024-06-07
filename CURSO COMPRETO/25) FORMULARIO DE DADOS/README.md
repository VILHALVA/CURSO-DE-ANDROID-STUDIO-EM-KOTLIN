# FORMULARIO DE DADOS
Para criar um formulário de dados em uma nova `Activity`, siga os passos abaixo:

## Criando a Nova Activity:
1. No Android Studio, clique com o botão direito na pasta `java` ou `kotlin` dentro do diretório `app`.
2. Selecione "New" -> "Activity" -> "Empty Activity" (ou o tipo de atividade desejado).
3. Na janela que aparecer, insira um nome para a nova `Activity`, por exemplo, "FormularioActivity".
4. Clique em "Finish" para criar a nova `Activity`.

## Layout XML:
Agora, você precisa definir o layout XML para o formulário de dados. Você pode adicionar elementos de interface do usuário (UI), como EditTexts, Spinners, Checkboxes, etc., conforme necessário. Aqui está um exemplo simples:

```xml
<!-- activity_formulario.xml -->
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".FormularioActivity">

    <EditText
        android:id="@+id/etNome"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nome"
        android:layout_margin="16dp" />

    <EditText
        android:id="@+id/etEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Email"
        android:inputType="textEmailAddress"
        android:layout_below="@id/etNome"
        android:layout_margin="16dp" />

    <Button
        android:id="@+id/btnEnviar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Enviar"
        android:layout_below="@id/etEmail"
        android:layout_centerHorizontal="true"
        android:layout_marginTop="16dp" />

</RelativeLayout>
```

## Lógica da Activity:
Agora, você precisa implementar a lógica da `Activity` para lidar com os dados inseridos pelo usuário. Você pode acessar os elementos da interface do usuário (UI) usando seus IDs e definir o comportamento do botão "Enviar". Aqui está um exemplo básico em Kotlin:

```kotlin
// FormularioActivity.kt
package com.example.seuapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.Toast

class FormularioActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_formulario)

        val etNome: EditText = findViewById(R.id.etNome)
        val etEmail: EditText = findViewById(R.id.etEmail)
        val btnEnviar: Button = findViewById(R.id.btnEnviar)

        btnEnviar.setOnClickListener {
            val nome = etNome.text.toString()
            val email = etEmail.text.toString()

            // Aqui você pode realizar validações ou enviar os dados para algum serviço, banco de dados, etc.
            
            // Exemplo: Exibir uma mensagem com os dados inseridos
            val mensagem = "Nome: $nome\nEmail: $email"
            Toast.makeText(this, mensagem, Toast.LENGTH_LONG).show()
        }
    }
}
```

Lembre-se de adicionar a nova `Activity` ao arquivo `AndroidManifest.xml` para que o Android Studio saiba que ela existe.

Depois de adicionar esses trechos de código, você terá um formulário de dados funcional em uma nova `Activity` no seu aplicativo Android.