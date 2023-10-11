# Parcial-SPD-
En este repositorio de Github se pueden encontrar la primera, la segunda y la tercera parte del primer parcial de SPD

## Integrantes: 
- Emiliano David Centurion
- Morena Castillo

# Proyecto_1 

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

https://www.tinkercad.com/things/211oPD8WYyH?sharecode=1s2QrgWYPXN5x4lo-f2UwmFbJqnRB6irPszFoTnPOPA

