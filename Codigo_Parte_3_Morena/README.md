# Parte 3 - Morena Castillo: 

![PARCIAL PARTE 3 SENSOR LUZ AMBIENTAL (2)](https://github.com/Emuardo/Parcial-SPD/assets/138258397/5f2ddce0-5a83-4802-8132-2255deb71a15)


# Descripcion: 
 Como parte adicional al proyecto de la parte dos, en mi caso debia adicionar un SENSOR DE LUZ AMBIENTAL, la logica tras implementar este instrumento en el circuito se basa en que si el motor se encuentra encendido y si la temperatura se encuentra en condiciones de funcionamiento (de 0° a 20°) la luz tenga la capacidad de encender siempre y cuando su valor sea mayor a 500, de forma contraria, puede prender todo menos la luz, de forma de que no interfiera en el  circuito con los contadores y displays

# Funcion principal del proyecto:

Mi funcion principal es "LOOP" en la cual (ademas de hacer toda la logica de la parte dos) implementa las condiciones de motor, temperatura, y valor de luz para que el sensor y el foco enciendan

~~~ C
void loop() {
  lectura = analogRead(SENSOR_TEMP);
  temperatura = map(lectura, 20, 358, -40, 125);
  posicionSwitch = digitalRead(INTERRUPTOR);
  int valorLuz = analogRead(SENSOR);
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
      digitalWrite(FOCO, LOW);
      Serial.println("Motor apagado");
      banderaPrendido = false;
    } else {
      Serial.println("INVALIDO, Ingrese opción correcta");
      
    }
  }

  if (banderaPrendido) {
    if (temperatura >= 0 && temperatura <= 20 && valorLuz > luzPrendida) {
      digitalWrite(FOCO, HIGH);
    } else {
      digitalWrite(FOCO, LOW);
    }
    if (temperatura >= 0 && temperatura <= 20) {
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
      digitalWrite(FOCO, LOW);
  }
 }
}

~~~

## :robot: Link al proyecto:

 [Proyecto](https://www.tinkercad.com/things/00aWOTFUBHQ)

