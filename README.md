# Parcial-SPD-
En este repositorio de Github se pueden encontrar la primera, la segunda y la tercera parte de cada uno de los integrantes del primer parcial de la materia Sistema de Procesamiento de Datos

## Integrantes: 
- Emiliano David Centurion
- Morena Castillo

# Parte 1: 

![PARCIAL (1)](https://github.com/Emuardo/Parcial-SPD-/assets/107709876/8dd4c809-1f01-46ee-9358-a1c972241b2a)


# Descripcion: 

- El proyecto es un contador de 0 a 99 hecho con dos displays de siete segmentos y tres botones, los cuales aumentan, disminuyen y reinician el proceso. Esto fue realizado utilizando el metodo de la multiplexacion el cual nos permite controlar cada uno de los displays

# Funcion principal del proyecto:

Nuestra funcion principal es "LOOP" en la cual se realiza el bucle principal del programa y se manejan los displays

~~~ C
void loop() 
{
    int presionado = botonPresionado();
    if(presionado == MAS) 
    {
        numero++;
        if(numero > 99)
            numero = 0;
    } 
    else if(presionado == MENOS) 
    {
        numero--;
        if(numero < 0)
            numero = 99;
    } 
    else if (presionado == RESET) 
    {
        numero = 0;
    }
  
 iniciarContador(numero);
}
~~~

## :robot: Link al proyecto:

 [Proyecto](https://www.tinkercad.com/things/211oPD8WYyH?sharecode=1s2QrgWYPXN5x4lo-f2UwmFbJqnRB6irPszFoTnPOPA)

# Parte 2:

 ![PARCIAL PARTE 2 MOTORES](https://github.com/Emuardo/Parcial-SPD-/assets/107709876/1fb6b24f-8fd8-475c-9315-2788177c8b54)

# Descripcion:

 - El proyecto es un contador de números enteros y primos que va de 0 a 99  hecho con dos diplays de siete segmentos, utilizamos dos botones los cuales aumentan y disminuyen numeros. Para validar cual de los contadores se quiere utilizar, lo realizamos mediante un interruptor, que dependiendo su estado, contara primos o enteros.
Por otro lado utilizamos motores y sensores de temperatura para condicionar el funcionamiento del circuito, es decir si el motor se encuentra encendido y la temperatura se encuentra entre 0° y 20°, todo el circuito funciona.

# Funcion principal del proyecto:

Nuentra funcion principal es el LOOP la cual tiene como objetivo ser el bucle principal del programa, dentro de ella se encuentran las condiciones de manejo del motor, la temperatura y los contadores de numeros enteros y primos

~~~ C
void loop() {
  lectura = analogRead(SENSOR);
  temperatura = map(lectura, 20, 358, -40, 125);
  posicionSwitch = digitalRead(INTERRUPTOR);
  int boton = botonPresionado();

  if (Serial.available() > 0) {
    opcion = Serial.read();
    if (opcion == '1') {
      Serial.println("Motor prendido (Temp. Funcionamiento -> 0 C a 20 C)");
      banderaPrendido = true;
    } else if (opcion == '2') {
      digitalWrite(MOTOR, LOW);
      digitalWrite(UNIDAD, HIGH);
      digitalWrite(DECENA, HIGH);
      Serial.println("Motor apagado");
      banderaPrendido = false;
    } else {
      Serial.println("INVALIDO, Ingrese opción correcta");
    }
  }

  if (banderaPrendido) {
    if (temperatura >= 0 && temperatura <= 20){
        if (posicionSwitch == HIGH) {
          if (boton == INCREMENTAR) {
            if (contadorEnteros < 100) {
              contadorEnteros++;
            } else {
              contadorEnteros = 0;
            }
          }
          if (boton == DECREMENTAR) {
            if (contadorEnteros > 0) {
              contadorEnteros--;
            } else {
              contadorEnteros = 99;
            }
          }
          mostrarNumeroEnteroEnDisplays();
    } else {
      if (boton == INCREMENTAR) {
        while (true) {
          if (contadorPrimos < 100) {
            contadorPrimos++;
            if (esPrimo(contadorPrimos)) {
              break;
            }
          } else {
            contadorPrimos = 2;
            break;
          }
        }
      }
      if (boton == DECREMENTAR) {
        while (true) {
          if (contadorPrimos > 2) {
            contadorPrimos--;
            if (esPrimo(contadorPrimos)) {
              break;
            }
          } else {
            contadorPrimos = 97;
            break;
          }
        }
      }
      mostrarNumeroPrimoEnDisplays();
    }
  }
  else{
      digitalWrite(UNIDAD, HIGH);
      digitalWrite(DECENA, HIGH);
  }
}
}

~~~

## :robot: Link al proyecto:

[Proyecto](https://www.tinkercad.com/things/3Pr4BMTk4Xz?sharecode=7UqGUWYF5dkLmTgSxbVc07WBP5TALihZQU5LAZrZz6Q)
