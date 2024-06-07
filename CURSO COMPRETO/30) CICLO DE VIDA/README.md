# CICLO DE VIDA
O ciclo de vida de uma Activity no Android é composto por uma série de estados que a Activity atravessa, desde sua criação até sua destruição. Aqui está uma visão geral dos principais estados do ciclo de vida de uma Activity:

1. **onCreate()**: Este método é chamado quando a Activity é criada pela primeira vez. É onde a inicialização básica ocorre, como a criação de layouts e a configuração de variáveis.

2. **onStart()**: Este método é chamado quando a Activity se torna visível para o usuário. Neste ponto, a Activity está prestes a se tornar interativa, mas ainda não está em foco.

3. **onResume()**: Este método é chamado quando a Activity está prestes a começar a interagir com o usuário. Neste ponto, a Activity está em primeiro plano e pode receber entrada do usuário.

4. **onPause()**: Este método é chamado quando outra Activity está prestes a ser iniciada e terá foco. Neste ponto, a Activity ainda é visível, mas não está mais em primeiro plano e não está recebendo entrada do usuário.

5. **onStop()**: Este método é chamado quando a Activity não está mais visível para o usuário. Neste ponto, a Activity está encoberta por outra Activity ou está sendo encerrada.

6. **onDestroy()**: Este método é chamado quando a Activity está prestes a ser destruída. É onde os recursos não utilizados devem ser liberados e as operações de limpeza devem ser realizadas.

Além desses métodos principais, existem outros eventos que podem ocorrer durante o ciclo de vida de uma Activity, como `onRestart()` (chamado quando a Activity está sendo reiniciada após ser parcialmente oculta), `onSaveInstanceState()` (chamado quando a Activity está prestes a ser destruída, mas pode ser recriada posteriormente) e `onRestoreInstanceState()` (chamado após `onStart()` para restaurar o estado da Activity após ter sido salvo).

É importante entender o ciclo de vida de uma Activity ao desenvolver aplicativos Android para garantir que as operações corretas sejam realizadas em cada estado da Activity e evitar vazamentos de memória e problemas de desempenho.