# trainee

package com.example.training

import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import androidx.activity.ComponentActivity

/**
 * 1) escribir programa con saludo.
 * 2) definir si es mayor de edad
 * 3) si es mayor y lleva mas de 6 meses jugando tenis o es profesor.
 * 4) multiplicar un numero
 * 5) sumar 2 numeros
 * 6) mostrar el mayor de los numeros
 * 7) guardar personas
 */


class MainActivity : ComponentActivity() {

    val listaEmpleados: MutableList<Empleado> = ArrayList()


    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.main_activity)
        val myString = "Hola tati"

        val firstEditText: EditText = findViewById(R.id.firstEditText)
        val secondEditText: EditText = findViewById(R.id.secondEditText)
        val thirdEditText: EditText = findViewById(R.id.thirdEditText)
        val resultTV = findViewById<TextView>(R.id.result)
        val button = findViewById<Button>(R.id.button)


        button.setOnClickListener {
            // cada vez que se hace click al boton.

            val nombreEmpleado: String = firstEditText.text.toString()
            val edad: Int = secondEditText.text.toString().toInt()

            val miEmpleado = Empleado(nombreEmpleado, edad, false)
            listaEmpleados.add(miEmpleado)


            var todosLosNombres: String = ""

            listaEmpleados.forEach { empleado ->
                todosLosNombres = todosLosNombres + " " + empleado.name
            }

            resultTV.text = todosLosNombres

            /*
          var nombreParaSaludo: String = firstEditText.text.toString()
          var saludo: String = "Hola, còmo estas " + nombreParaSaludo
          resultTV.text = saludo

          if (edad >= 18) {
              var edadmayor: String = "Eres mayor de edad " + nombreParaSaludo
              resultTV.text = edadmayor
          } else {
              var edadmenor: String = "Eres menor de edad " + nombreParaSaludo
              resultTV.text = edadmenor
          }*/
        }
    }
}

data class Empleado(val name: String, val age: Int, val isMarried: Boolean)


<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:id="@+id/result"
        android:gravity="center"
        android:text="Result"/>

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/firstEditText"/>

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/secondEditText"/>


    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/thirdEditText"/>

    <Button
        android:layout_height="wrap_content"
        android:layout_width="match_parent"
        android:id="@+id/button"
        android:text="Submit" />

</LinearLayout>
