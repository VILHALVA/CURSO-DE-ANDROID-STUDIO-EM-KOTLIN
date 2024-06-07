# ROOM
Room é uma biblioteca oficial do Android que fornece uma camada de abstração sobre o SQLite, facilitando a criação e o gerenciamento de bancos de dados locais no Android. Ela simplifica a interação com o SQLite ao mesmo tempo em que oferece um alto nível de flexibilidade e poder.

Aqui está um exemplo básico de como usar o Room em um aplicativo Android para criar e acessar um banco de dados local:

## 1. Definir a Entidade:
```kotlin
// Contact.kt
import androidx.room.Entity
import androidx.room.PrimaryKey

@Entity(tableName = "contacts")
data class Contact(
    @PrimaryKey(autoGenerate = true)
    val id: Long = 0,
    val name: String,
    val phoneNumber: String
)
```

## 2. Criar o DAO (Data Access Object):
```kotlin
// ContactDao.kt
import androidx.room.Dao
import androidx.room.Insert
import androidx.room.Query

@Dao
interface ContactDao {
    @Query("SELECT * FROM contacts")
    fun getAll(): List<Contact>

    @Insert
    fun insert(contact: Contact)
}
```

## 3. Criar o Banco de Dados:
```kotlin
// AppDatabase.kt
import androidx.room.Database
import androidx.room.RoomDatabase

@Database(entities = [Contact::class], version = 1)
abstract class AppDatabase : RoomDatabase() {
    abstract fun contactDao(): ContactDao
}
```

## 4. Inicializar e Usar o Banco de Dados na Activity:
```kotlin
// MainActivity.kt
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.lifecycle.lifecycleScope
import androidx.room.Room
import com.example.myapp.databinding.ActivityMainBinding
import kotlinx.coroutines.Dispatchers
import kotlinx.coroutines.launch
import kotlinx.coroutines.withContext

class MainActivity : AppCompatActivity() {

    private lateinit var binding: ActivityMainBinding
    private lateinit var db: AppDatabase

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        db = Room.databaseBuilder(
            applicationContext,
            AppDatabase::class.java, "app-database"
        ).build()

        lifecycleScope.launch {
            insertData()
            displayData()
        }
    }

    private suspend fun insertData() {
        withContext(Dispatchers.IO) {
            db.contactDao().insert(Contact(name = "John", phoneNumber = "123456789"))
        }
    }

    private suspend fun displayData() {
        val contacts = withContext(Dispatchers.IO) {
            db.contactDao().getAll()
        }
        // Exibir os contatos na interface do usuário
    }
}
```

Este é um exemplo básico de como usar o Room para criar e acessar um banco de dados local no Android. Ele inclui a definição da entidade, o DAO para acessar os dados, a classe do banco de dados e a inicialização e uso do banco de dados na Activity. Você pode expandir este exemplo adicionando mais funcionalidades, como atualização e exclusão de dados, ou implementando consultas mais complexas.