# LISTA DE NOMES
Para criar uma lista de nomes em uma nova `Activity`, você pode seguir um processo semelhante ao da criação do formulário de dados. Aqui está um exemplo de como você pode fazer isso:

## Criando a Nova Activity:
1. No Android Studio, clique com o botão direito na pasta `java` ou `kotlin` dentro do diretório `app`.
2. Selecione "New" -> "Activity" -> "Empty Activity" (ou o tipo de atividade desejado).
3. Na janela que aparecer, insira um nome para a nova `Activity`, por exemplo, "ListaNomesActivity".
4. Clique em "Finish" para criar a nova `Activity`.

## Layout XML:
Defina o layout XML para exibir a lista de nomes. Você pode usar um componente ListView ou RecyclerView para isso. Aqui está um exemplo usando RecyclerView:

```xml
<!-- activity_lista_nomes.xml -->
<?xml version="1.0" encoding="utf-8"?>
<androidx.recyclerview.widget.RecyclerView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/recyclerView"
    android:layout_width="match_parent"
    android:layout_height="match_parent" />
```

## Lógica da Activity:
Implemente a lógica da `Activity` para exibir a lista de nomes. Você precisará criar um adapter para vincular os dados à RecyclerView. Aqui está um exemplo básico em Kotlin:

```kotlin
// ListaNomesActivity.kt
package com.example.seuapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import androidx.recyclerview.widget.LinearLayoutManager
import androidx.recyclerview.widget.RecyclerView

class ListaNomesActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_lista_nomes)

        val recyclerView: RecyclerView = findViewById(R.id.recyclerView)
        recyclerView.layoutManager = LinearLayoutManager(this)

        val nomes = listOf("João", "Maria", "José", "Ana", "Pedro", "Carla", "Paulo", "Fernanda")

        val adapter = NomesAdapter(nomes)
        recyclerView.adapter = adapter
    }
}
```

## Adapter:
Você também precisará criar um adapter para a RecyclerView. Aqui está um exemplo básico de um adapter simples:

```kotlin
// NomesAdapter.kt
package com.example.seuapp

import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.TextView
import androidx.recyclerview.widget.RecyclerView

class NomesAdapter(private val nomes: List<String>) : RecyclerView.Adapter<NomesAdapter.ViewHolder>() {

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val view = LayoutInflater.from(parent.context).inflate(android.R.layout.simple_list_item_1, parent, false)
        return ViewHolder(view)
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        val nome = nomes[position]
        holder.bind(nome)
    }

    override fun getItemCount(): Int {
        return nomes.size
    }

    class ViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
        private val textView: TextView = itemView.findViewById(android.R.id.text1)

        fun bind(nome: String) {
            textView.text = nome
        }
    }
}
```

Depois de adicionar esses trechos de código, você terá uma `Activity` que exibe uma lista de nomes usando RecyclerView em seu aplicativo Android. Certifique-se de ter os layouts XML e classes Kotlin ou Java corretamente configurados.