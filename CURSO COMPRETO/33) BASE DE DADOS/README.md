# BASE DE DADOS
Para criar e gerenciar uma base de dados em um aplicativo Android, você pode usar o SQLite, que é uma biblioteca leve de banco de dados relacional incorporada no Android. Aqui estão os passos básicos para trabalhar com o SQLite em um aplicativo Android:

## 1. Criar um Helper de Banco de Dados:
Você precisará criar uma classe que estende `SQLiteOpenHelper` para criar e atualizar seu banco de dados.

```kotlin
import android.content.Context
import android.database.sqlite.SQLiteDatabase
import android.database.sqlite.SQLiteOpenHelper

class DatabaseHelper(context: Context) : SQLiteOpenHelper(context, DATABASE_NAME, null, DATABASE_VERSION) {

    companion object {
        private const val DATABASE_NAME = "MyDatabase"
        private const val DATABASE_VERSION = 1
        // Defina as constantes para o nome das tabelas, colunas, etc.
    }

    override fun onCreate(db: SQLiteDatabase) {
        // Criação da estrutura do banco de dados (tabelas, índices, etc.)
        db.execSQL("CREATE TABLE IF NOT EXISTS my_table (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT)")
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        // Atualização do banco de dados conforme necessário
        db.execSQL("DROP TABLE IF EXISTS my_table")
        onCreate(db)
    }
}
```

## 2. Executar Operações de Banco de Dados:
Use métodos da classe SQLiteDatabase para executar operações CRUD (Create, Read, Update, Delete) no banco de dados.

```kotlin
import android.content.ContentValues
import android.content.Context
import android.database.Cursor
import android.database.sqlite.SQLiteDatabase

class DatabaseManager(context: Context) {

    private val dbHelper = DatabaseHelper(context)
    
    fun insertData(name: String) {
        val db = dbHelper.writableDatabase
        val values = ContentValues().apply {
            put("name", name)
        }
        db.insert("my_table", null, values)
        db.close()
    }

    fun getAllData(): List<String> {
        val db = dbHelper.readableDatabase
        val cursor = db.rawQuery("SELECT * FROM my_table", null)
        val dataList = mutableListOf<String>()
        if (cursor.moveToFirst()) {
            do {
                val name = cursor.getString(cursor.getColumnIndex("name"))
                dataList.add(name)
            } while (cursor.moveToNext())
        }
        cursor.close()
        db.close()
        return dataList
    }
    
    // Implemente métodos para atualizar, excluir, pesquisar dados, etc. conforme necessário
}
```

## 3. Usar a Base de Dados na Activity ou Fragmento:
Use a classe `DatabaseManager` para executar operações de banco de dados na sua Activity ou Fragmento.

```kotlin
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val dbManager = DatabaseManager(this)
        dbManager.insertData("John Doe")
        
        val dataList = dbManager.getAllData()
        for (data in dataList) {
            println(data)
        }
    }
}
```

Certifique-se de adicionar as permissões necessárias no arquivo `AndroidManifest.xml` para acessar o banco de dados SQLite.

Este é um exemplo básico de como criar e gerenciar uma base de dados SQLite em um aplicativo Android. Você pode expandir esse exemplo adicionando mais tabelas, colunas, índices, relações, etc., conforme necessário para atender aos requisitos do seu aplicativo.