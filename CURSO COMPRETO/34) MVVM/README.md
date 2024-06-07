# MVVM
O MVVM (Model-View-ViewModel) é uma arquitetura de software que separa as responsabilidades em três componentes principais: Model, View e ViewModel. Aqui está uma explicação básica de cada componente:

1. **Model**:
   - Representa os dados e a lógica de negócios do aplicativo.
   - Pode incluir classes que representam entidades de negócios, classes de acesso a dados (por exemplo, para interagir com o banco de dados) e classes de repositório para abstrair o acesso aos dados.

2. **View**:
   - É a camada de interface do usuário (UI) que exibe os dados ao usuário e captura a entrada do usuário.
   - Geralmente, é implementada usando XML para definir layouts de tela e Kotlin/Java para controlar a interação com o usuário.

3. **ViewModel**:
   - Atua como um intermediário entre a View e o Model.
   - Mantém e fornece dados para a View.
   - Geralmente, contém lógica de apresentação que prepara os dados para serem exibidos na View.
   - Sobrevive a mudanças de configuração (como rotações de tela) e não está vinculado ao ciclo de vida da View.

A principal vantagem do MVVM é a separação clara de preocupações, o que facilita a manutenção e o teste do código. Aqui está um exemplo básico de como implementar o MVVM em um aplicativo Android:

## Exemplo de Implementação MVVM:
1. **Model**:
   - Crie classes que representam os dados do aplicativo e a lógica de negócios.

```kotlin
data class User(val id: Int, val name: String)
```

2. **ViewModel**:
   - Crie uma classe ViewModel que fornecerá dados para a View.

```kotlin
import androidx.lifecycle.ViewModel

class UserViewModel : ViewModel() {
    // Simula a obtenção de dados do Model
    fun getUsers(): List<User> {
        return listOf(User(1, "John"), User(2, "Alice"), User(3, "Bob"))
    }
}
```

3. **View**:
   - Implemente a interface do usuário e associe-a ao ViewModel usando arquitetura de componentes.

```xml
<!-- activity_main.xml -->
<androidx.recyclerview.widget.RecyclerView
    android:id="@+id/recyclerView"
    android:layout_width="match_parent"
    android:layout_height="match_parent"/>
```

```kotlin
// MainActivity.kt
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity
import androidx.lifecycle.ViewModelProvider
import androidx.recyclerview.widget.LinearLayoutManager
import com.example.myapp.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {

    private lateinit var binding: ActivityMainBinding
    private lateinit var userViewModel: UserViewModel
    private lateinit var adapter: UserAdapter

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)

        userViewModel = ViewModelProvider(this).get(UserViewModel::class.java)

        adapter = UserAdapter(userViewModel.getUsers())
        binding.recyclerView.layoutManager = LinearLayoutManager(this)
        binding.recyclerView.adapter = adapter
    }
}
```

Neste exemplo, a ViewModel fornece os dados do usuário para a View (RecyclerView) e a View é responsável por exibir os dados na tela. A separação de preocupações facilita a manutenção e o teste do código.