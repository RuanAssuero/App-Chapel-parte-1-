# App-Chapel-parte-1-
package com.example.chapeuseletor

import android.os.Bundle
import android.widget.Button
import android.widget.RadioGroup
import android.widget.Toast
import androidx.activity.enableEdgeToEdge
import androidx.appcompat.app.AppCompatActivity
import androidx.core.view.ViewCompat
import androidx.core.view.WindowInsetsCompat

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
       
        val radioGroup = findViewById<RadioGroup>(R.id.radioGroupCasas)
        val button = findViewById<Button>(R.id.btnSortear)
        button.setOnClickListener {
           
            val idSelecionado = radioGroup.checkedRadioButtonId
            
            if (idSelecionado == -1) {
                Toast.makeText(this, "Por favor, selecione uma opção!", Toast.LENGTH_SHORT).show()
            } else {
                
                val casa = when (idSelecionado) {
                    R.id.radioCoragem -> "Grifinória!"
                    R.id.radioSabedoria -> "Corvinal!"
                    R.id.radioAmbicao -> "Sonserina!"
                    R.id.radioLealdade -> "Lufa-Lufa!"
                    else -> "Casa Indefinida" // Caso de segurança, não deve acontecer
                }
                Toast.makeText(this, "Você pertence à... $casa", Toast.LENGTH_LONG).show()
            }
        }
    }
}
