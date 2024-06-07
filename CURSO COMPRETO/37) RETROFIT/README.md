# RETROFIT
Retrofit é uma biblioteca de cliente HTTP para Android e Java que facilita a criação de aplicativos que se comunicam com serviços da web. Ela simplifica o processo de fazer solicitações de rede em aplicativos Android, tornando mais fácil consumir APIs da web e processar os dados recebidos.

Aqui está um exemplo básico de como usar o Retrofit para fazer uma solicitação GET para uma API da web e processar os dados recebidos em um aplicativo Android:

## 1. Adicionar Dependência:
Adicione a dependência Retrofit ao seu arquivo `build.gradle`:

```groovy
implementation 'com.squareup.retrofit2:retrofit:2.9.0'
```

## 2. Definir o Modelo de Dados:
```kotlin
// User.kt
data class User(
    val id: Int,
    val name: String,
    val email: String
)
```

## 3. Criar a Interface de Serviço:
```kotlin
// ApiService.kt
import retrofit2.http.GET

interface ApiService {

    @GET("users")
    suspend fun getUsers(): List<User>
}
```

## 4. Configurar o Retrofit:
```kotlin
// RetrofitClient.kt
import retrofit2.Retrofit
import retrofit2.converter.gson.GsonConverterFactory

object RetrofitClient {

    private const val BASE_URL = "https://jsonplaceholder.typicode.com/"

    val apiService: ApiService by lazy {
        val retrofit = Retrofit.Builder()
            .baseUrl(BASE_URL)
            .addConverterFactory(GsonConverterFactory.create())
            .build()

        retrofit.create(ApiService::class.java)
    }
}
```

## 5. Fazer a Solicitação na Activity ou Fragmento:
```kotlin
// MainActivity.kt
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import kotlinx.coroutines.Dispatchers
import kotlinx.coroutines.GlobalScope
import kotlinx.coroutines.launch

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        GlobalScope.launch(Dispatchers.Main) {
            val users = RetrofitClient.apiService.getUsers()
            // Processar os dados recebidos (por exemplo, exibir em uma RecyclerView)
        }
    }
}
```

Este é um exemplo básico de como usar o Retrofit para fazer uma solicitação GET para uma API da web e processar os dados recebidos em um aplicativo Android. Você pode expandir este exemplo adicionando mais funcionalidades, como manipulação de erros, passagem de parâmetros para a solicitação, ou implementando solicitações POST, PUT, DELETE, etc.