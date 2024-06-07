# CONVERSOR DE DOLAR REAL E EURO
Para criar um aplicativo que converta valores entre dólar, euro e real, precisaremos de um layout com três EditTexts para entrada de valores, botões para selecionar a moeda de origem e de destino, e um TextView para exibir o resultado da conversão. Aqui estão os trechos de código Kotlin e XML para isso:

## Criando o Projeto no Android Studio:
1. Abra o Android Studio.
2. Selecione "Create New Project" no menu inicial.
3. Escolha "Empty Activity" e clique em "Next".
4. Dê um nome ao seu projeto, como "ConversorMoedas", e clique em "Finish".

Agora, vamos adicionar os trechos de código necessários.

## Trecho de Código Kotlin (MainActivity.kt):
Este código será responsável por realizar a conversão de valores entre dólar, euro e real, de acordo com a seleção do usuário.

```kotlin
package com.example.conversormoedas

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val etValor: EditText = findViewById(R.id.etValor)
        val btnConverter: Button = findViewById(R.id.btnConverter)
        val spinnerOrigem: Spinner = findViewById(R.id.spinnerOrigem)
        val spinnerDestino: Spinner = findViewById(R.id.spinnerDestino)
        val tvResultado: TextView = findViewById(R.id.tvResultado)

        // Lista de moedas disponíveis
        val moedas = arrayOf("Dólar", "Euro", "Real")

        // Adaptadores para os spinners
        val adapter = ArrayAdapter(this, android.R.layout.simple_spinner_item, moedas)
        adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)

        spinnerOrigem.adapter = adapter
        spinnerDestino.adapter = adapter

        btnConverter.setOnClickListener {
            val valor = etValor.text.toString().toDouble()

            // Taxas de conversão fictícias para exemplificação
            val taxaDolar = 5.2
            val taxaEuro = 6.2

            // Seleciona a moeda de origem e de destino
            val origem = spinnerOrigem.selectedItem.toString()
            val destino = spinnerDestino.selectedItem.toString()

            // Realiza a conversão
            val resultado = when (origem) {
                "Dólar" -> when (destino) {
                    "Dólar" -> valor
                    "Euro" -> valor * (1 / taxaDolar) * taxaEuro
                    "Real" -> valor * taxaDolar
                    else -> valor
                }
                "Euro" -> when (destino) {
                    "Dólar" -> valor * (1 / taxaEuro) * taxaDolar
                    "Euro" -> valor
                    "Real" -> valor * taxaEuro
                    else -> valor
                }
                "Real" -> when (destino) {
                    "Dólar" -> valor * (1 / taxaDolar)
                    "Euro" -> valor * (1 / taxaEuro)
                    "Real" -> valor
                    else -> valor
                }
                else -> valor
            }

            tvResultado.text = "Resultado: ${String.format("%.2f", resultado)} $destino"
        }
    }
}
```

## Trecho de Código XML (activity_main.xml):
Este arquivo XML define a interface do usuário (UI) da nossa atividade principal, com EditText para o valor, spinners para seleção da moeda de origem e de destino, botão para iniciar a conversão e TextView para exibir o resultado.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/etValor"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Valor"
        android:inputType="numberDecimal"
        android:layout_margin="16dp" />

    <Spinner
        android:id="@+id/spinnerOrigem"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/etValor"
        android:layout_marginStart="16dp"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="8dp" />

    <Spinner
        android:id="@+id/spinnerDestino"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/etValor"
        android:layout_toEndOf="@id/spinnerOrigem"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp" />

    <Button
        android:id="@+id/btnConverter"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Converter"
        android:layout_below="@id/spinnerOrigem"
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
- **MainActivity.kt**: `app/src/main/java/com/example/conversormoedas/MainActivity.kt`
- **activity_main.xml**: `app/src/main/res/layout/activity_main.xml`

Após adicionar esses trechos de código aos arquivos correspondentes, você pode executar o aplicativo no emulador ou em um dispositivo Android e testar a conversão entre dólar, euro e real.