# RECYCLER VIEW
Para criar um aplicativo Android com RecyclerView, que exibe uma lista de itens em um layout de lista, siga estas etapas:

## 1. Defina o layout do item da lista:
Crie um layout XML que represente um único item da lista. Por exemplo, se você estiver exibindo uma lista de textos simples, pode criar um layout simples com um TextView:

```xml
<!-- item_layout.xml -->
<TextView
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:id="@+id/textViewItem"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:textSize="18sp"
    android:padding="10dp"/>
```

## 2. Crie uma classe para representar os dados do item:
Crie uma classe para representar os dados que serão exibidos em cada item da lista. Por exemplo, se você estiver exibindo uma lista de strings, pode criar uma classe simples como esta:

```kotlin
// Item.kt
data class Item(val text: String)
```

## 3. Implemente o adapter:
Crie um adapter para conectar os dados à RecyclerView. Este adapter infla o layout do item da lista e vincula os dados aos elementos de visualização.

```kotlin
// Adapter.kt
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.TextView
import androidx.recyclerview.widget.RecyclerView

class Adapter(private val items: List<Item>) : RecyclerView.Adapter<Adapter.ViewHolder>() {

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val view = LayoutInflater.from(parent.context).inflate(R.layout.item_layout, parent, false)
        return ViewHolder(view)
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        val item = items[position]
        holder.textViewItem.text = item.text
    }

    override fun getItemCount(): Int {
        return items.size
    }

    inner class ViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
        val textViewItem: TextView = itemView.findViewById(R.id.textViewItem)
    }
}
```

## 4. Configure a RecyclerView na sua Activity ou Fragmento:
Configure a RecyclerView na sua Activity ou Fragmento e defina o adapter criado anteriormente.

```kotlin
// MainActivity.kt
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.recyclerview.widget.LinearLayoutManager
import androidx.recyclerview.widget.RecyclerView

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val recyclerView: RecyclerView = findViewById(R.id.recyclerView)
        recyclerView.layoutManager = LinearLayoutManager(this)

        val items = listOf(Item("Item 1"), Item("Item 2"), Item("Item 3"))

        val adapter = Adapter(items)
        recyclerView.adapter = adapter
    }
}
```

## 5. Execute o aplicativo:
Compile e execute o aplicativo no dispositivo ou emulador Android. Você deve ver uma lista de itens sendo exibidos na RecyclerView.

Essas são as etapas básicas para criar um aplicativo Android com RecyclerView. Você pode personalizar o layout do item da lista, os dados exibidos, o comportamento do adapter e a aparência da RecyclerView de acordo com as necessidades do seu aplicativo.