# AUDIO - MEDIA PLAYER
Para reproduzir áudio em um aplicativo Android usando o `MediaPlayer`, siga estas etapas:

## 1. Adicione o arquivo de áudio ao diretório de recursos:
   - Copie o arquivo de áudio (por exemplo, `audio.mp3`) para o diretório `res/raw` do seu projeto.

## 2. Inicie o MediaPlayer na Activity ou Fragmento:
   - No código Kotlin ou Java da sua Activity ou Fragmento, crie e configure o `MediaPlayer` para reproduzir o áudio:

```kotlin
import android.media.MediaPlayer
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    private lateinit var mediaPlayer: MediaPlayer

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Inicializa o MediaPlayer com o arquivo de áudio
        mediaPlayer = MediaPlayer.create(this, R.raw.audio)

        // Inicia a reprodução quando o usuário clicar em algum botão ou realizar outra ação
        // Por exemplo, você pode iniciar a reprodução quando o usuário clicar em um botão
        // Aqui está um exemplo básico:
        findViewById<Button>(R.id.btnPlay).setOnClickListener {
            if (!mediaPlayer.isPlaying) {
                mediaPlayer.start()
            }
        }
        
        // Pausa a reprodução quando o usuário clicar em outro botão, ou quando a reprodução terminar
        // Aqui está um exemplo básico:
        findViewById<Button>(R.id.btnPause).setOnClickListener {
            if (mediaPlayer.isPlaying) {
                mediaPlayer.pause()
            }
        }
    }

    override fun onDestroy() {
        super.onDestroy()
        // Libera os recursos do MediaPlayer quando a Activity é destruída para evitar vazamentos de memória
        mediaPlayer.release()
    }
}
```

## 3. Adicione Botões na Interface do Usuário:
   - No layout XML da sua Activity ou Fragmento, adicione botões para controlar a reprodução do áudio:

```xml
<Button
    android:id="@+id/btnPlay"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Play" />

<Button
    android:id="@+id/btnPause"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Pause" />
```

## 4. Execute o Aplicativo:
   - Compile e execute o aplicativo no dispositivo ou emulador Android.
   - Quando o usuário clicar no botão "Play", o áudio será reproduzido. Quando o usuário clicar no botão "Pause", a reprodução será pausada.

Lembre-se de substituir `R.raw.audio` pelo ID do seu arquivo de áudio em `res/raw`. Este é um exemplo básico para iniciar a reprodução de áudio usando o `MediaPlayer`. Você pode adicionar mais funcionalidades, como controle de volume, progresso da reprodução, etc., conforme necessário.