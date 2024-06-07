# LAYOUT RELATIVE
O RelativeLayout é um layout bastante flexível que permite posicionar os elementos com base nas relações entre eles e com as bordas do layout pai. Aqui está um exemplo de como usar RelativeLayout em um arquivo XML de layout:

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/textView1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Texto 1"
        android:layout_marginStart="16dp"
        android:layout_marginTop="16dp" />

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Texto 2"
        android:layout_below="@id/textView1"
        android:layout_marginStart="16dp"
        android:layout_marginTop="16dp" />

    <Button
        android:id="@+id/button1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Botão 1"
        android:layout_below="@id/textView2"
        android:layout_alignParentEnd="true"
        android:layout_marginTop="16dp"
        android:layout_marginEnd="16dp" />

    <Button
        android:id="@+id/button2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Botão 2"
        android:layout_below="@id/button1"
        android:layout_alignStart="@id/button1"
        android:layout_marginTop="16dp" />

</RelativeLayout>
```

Neste exemplo:
- O primeiro TextView (`textView1`) está alinhado à margem superior e à margem inicial (start) do layout.
- O segundo TextView (`textView2`) está alinhado abaixo do primeiro TextView e à margem inicial (start) do layout.
- O primeiro Button (`button1`) está alinhado abaixo do segundo TextView e à margem final (end) do layout.
- O segundo Button (`button2`) está alinhado abaixo do primeiro Button e à mesma margem inicial (start) do primeiro Button.

Este é apenas um exemplo simples de como usar o RelativeLayout. Com este layout, os elementos serão posicionados de acordo com as relações especificadas entre eles e as bordas do layout pai. Experimente diferentes atributos de layout para criar layouts mais complexos com RelativeLayout.