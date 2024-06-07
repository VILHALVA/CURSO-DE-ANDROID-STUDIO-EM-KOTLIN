# APP LISTA TELEFONICA
Para criar um aplicativo de lista telefônica simples usando a arquitetura MVVM, você pode seguir as etapas abaixo:

## 1. Definir o Modelo:
```kotlin
// Contact.kt
data class Contact(val id: Int, val name: String, val phoneNumber: String)
```

## 2. Implementar a Camada ViewModel:
```kotlin
// ContactViewModel.kt
import androidx.lifecycle.ViewModel

class ContactViewModel : ViewModel() {
    private val contacts = mutableListOf<Contact>()

    init {
        // Inicialize alguns contatos de exemplo
        contacts.add(Contact(1, "João", "123456789"))
        contacts.add(Contact(2, "Maria", "987654321"))
        // Adicione mais contatos conforme necessário
    }

    fun getContacts(): List<Contact> {
        return contacts
    }
}
```

## 3. Criar a Interface do Usuário (View):
```xml
<!-- activity_main.xml -->
<androidx.recyclerview.widget.RecyclerView
    android:id="@+id/recyclerView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"/>
```

## 4. Implementar o Adaptador:
```kotlin
// ContactAdapter.kt
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.TextView
import androidx.recyclerview.widget.RecyclerView

class ContactAdapter(private val contacts: List<Contact>) : RecyclerView.Adapter<ContactAdapter.ViewHolder>() {

    override fun onCreateViewHolder(parent: ViewGroup, viewType: Int): ViewHolder {
        val view = LayoutInflater.from(parent.context).inflate(android.R.layout.simple_list_item_2, parent, false)
        return ViewHolder(view)
    }

    override fun onBindViewHolder(holder: ViewHolder, position: Int) {
        val contact = contacts[position]
        holder.nameTextView.text = contact.name
        holder.phoneNumberTextView.text = contact.phoneNumber
    }

    override fun getItemCount(): Int {
        return contacts.size
    }

    inner class ViewHolder(itemView: View) : RecyclerView.ViewHolder(itemView) {
        val nameTextView: TextView = itemView.findViewById(android.R.id.text1)
        val phoneNumberTextView: TextView = itemView.findViewById(android.R.id.text2)
    }
}
```

## 5. Conectar a View ao ViewModel:
```kotlin
// MainActivity.kt
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.lifecycle.ViewModelProvider
import androidx.recyclerview.widget.LinearLayoutManager
import com.example.myapp.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {

    private lateinit var binding: ActivityMainBinding
    private lateinit var contactViewModel: ContactViewModel
    private lateinit var adapter: ContactAdapter

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        contactViewModel = ViewModelProvider(this).get(ContactViewModel::class.java)

        adapter = ContactAdapter(contactViewModel.getContacts())
        binding.recyclerView.layoutManager = LinearLayoutManager(this)
        binding.recyclerView.adapter = adapter
    }
}
```

Este é um exemplo básico de como criar um aplicativo de lista telefônica usando a arquitetura MVVM no Android. Ele exibirá uma lista de contatos na tela usando RecyclerView. Você pode personalizar e expandir este exemplo adicionando mais recursos, como funcionalidades de adicionar, editar e excluir contatos, ou até mesmo integrar com uma base de dados real.