# GOOGLE MAPS
Para integrar o Google Maps em um aplicativo Android, siga estas etapas:

## 1. Obter uma Chave da API do Google Maps:
   - Acesse a [Console do Google Cloud](https://console.cloud.google.com/).
   - Crie um novo projeto ou selecione um existente.
   - No painel de navegação, selecione "APIs e Serviços" > "Credenciais".
   - Clique em "Criar credenciais" e selecione "Chave da API".
   - Copie a chave da API gerada.

## 2. Adicionar a Chave da API ao Manifesto do Aplicativo:
   - Abra o arquivo `AndroidManifest.xml`.
   - Adicione a permissão de acesso à internet dentro do elemento `<manifest>`:
     ```xml
     <uses-permission android:name="android.permission.INTERNET" />
     ```
   - Adicione a chave da API do Google Maps como uma meta-tag dentro do elemento `<application>`, substituindo `YOUR_API_KEY` pela sua chave:
     ```xml
     <meta-data
         android:name="com.google.android.geo.API_KEY"
         android:value="YOUR_API_KEY" />
     ```

## 3. Adicionar o Mapa à Interface do Usuário:
   - Abra o layout XML onde deseja exibir o mapa.
   - Adicione um fragmento do mapa usando a tag `<fragment>` e atribua um ID, como `map`, e defina o tamanho desejado:
     ```xml
     <fragment
         android:id="@+id/map"
         android:name="com.google.android.gms.maps.SupportMapFragment"
         android:layout_width="match_parent"
         android:layout_height="match_parent" />
     ```

## 4. Configurar o Mapa na Activity ou Fragmento:
   - No arquivo Kotlin ou Java da sua Activity ou Fragmento, configure o mapa:
     ```kotlin
     import androidx.appcompat.app.AppCompatActivity
     import android.os.Bundle
     import com.google.android.gms.maps.SupportMapFragment
     import com.google.android.gms.maps.OnMapReadyCallback

     class MapsActivity : AppCompatActivity(), OnMapReadyCallback {

         override fun onCreate(savedInstanceState: Bundle?) {
             super.onCreate(savedInstanceState)
             setContentView(R.layout.activity_maps)

             val mapFragment = supportFragmentManager.findFragmentById(R.id.map) as SupportMapFragment
             mapFragment.getMapAsync(this)
         }

         override fun onMapReady(googleMap: GoogleMap) {
             // Configurações iniciais do mapa
             val sydney = LatLng(-33.852, 151.211)
             googleMap.addMarker(MarkerOptions().position(sydney).title("Marker in Sydney"))
             googleMap.moveCamera(CameraUpdateFactory.newLatLng(sydney))
         }
     }
     ```

## 5. Executar o Aplicativo:
   - Compile e execute o aplicativo no dispositivo ou emulador Android.

Certifique-se de que sua chave da API do Google Maps esteja configurada corretamente e que você tenha permissões de internet no seu aplicativo. Isso permitirá que você integre o Google Maps com sucesso no seu aplicativo Android.