Orientación a Objetos 2 -Práctica 5
====================================

Ejercicio 1:  Refactoring
-------------------------

Indique si cada una de las siguientes aseveraciones es verdadera o falsa.
Explique.

  1. Cuando un código es refactorizado cambia su comportamiento agregando más
     funcionalidad.

  > FALSO: No cambia el comportamiento ni agrega más funcionalidad, mejora su
  > estructura interna. El comportamiento    no se altera, mejora la
  > legibilidad, adaptabilidad, mantenibilidad y organización del código.

  2. Si el código está bien refactorizado no es necesario testearlo.

  > FALSO: (por ej) Al refactorizar el código puede que se renombren métodos.
  > Si no se testea el código antes de ponerse en funcionamiento puede que el
  > código este haciendo llamadas a los viejos métodos y no a los nuevos.
  > (diapositiva 63).

  3. Después de ser refactorizado, la estructura interna del código permanece
     igual que antes.

  > FALSO: Al refactorizar el código es justamente la estructura interna lo que
  > cambia.

  4. La refactorización del código se hace en un sólo paso en el que se unen
     todos los cambios

  > FALSO: Existen pasos a respetar dependiendo el “tipo” de mal olor que se
  > refactorice. (código duplicado, métodos largos, clases grandes, muchos
  > parámetros, etc)


Ejercicio 2: Software con olores
--------------------------------

Responda:

  1. Qué significa la expresión “código con mal olor” según lo visto en la
     teoría?.

  > Significa que al ver un código el mismo no es fácil de leer para
  > entenderlo, de mantenerlo, de adaptarlo.

  2. Encuentre tres casos de los “malos olores” explicados en la teoría en su
     propio código de los prácticos anteriores.

  3. Indique tres razones por las cuales es importante hacer refactoring.

  > Es una defensa contra el deterioro del software. Facilita la incorporación
  > de código. Permite agregar patrones después de haber escrito el código, y
  > luego transformar un programa en un framework.



Ejercicio 3: Algo huele mal
---------------------------

Indique en los siguientes ejemplos la presencia de malos olores.

1. El diagrama de la figura 1 muestra que existen dos métodos en diferentes
   subclases que realizan algunos pasos similares en el mismo orden, aunque los
   pasos difieren entre sí. Aplicando lo que ya conoce de patrones, ¿cómo puede
   mejorar el diseño y el código? Realice el nuevo diagrama de clases.

  Utilice el código que se entrega en el material adicional de la práctica.
  Verifique que el código original, que responde al diagrama de clases de la
  figura pasa exitosamente los test cases. Haga las modificaciones que se piden
  al diseño, implemente los cambios al codigo de las clases Inmueble,
  ViviendaUnica y CasaFinDeSemana. Verifique que el nuevo código también pasa
  exitosamente los tests.

  ![ejer3-1](img/p5/ejer3-1.png)

  > Solucion Fran:
    [Paquete Ejercicio 3](src/p5 francisco/)


  2. La clase Cliente tiene el siguiente protocolo público. ¿Cómo puede
     mejorarlo?

  ```smalltalk
  # lmtCrdt devuelve el límite de crédito del cliente.

  # mtFcE: unaFecha y: otraFecha devuelve el monto facturado al cliente desde
  unaFecha hasta otraFecha

  # mtCbE: unaFecha y: aux devuelve el monto cobrado al cliente desde unaFecha
  hasta otraFecha
  ```
  > Los nombres de los métodos no son claros. Esto es muy subjetivo, yo pondría
  > estos nombres:

  ```smalltalk
    #limiteDeCredito
    #montoFacturadoEntre: fechaInicio y: fechaFin
    #montoFacturadoEntre: fechaInicio y: fechaFin
  ```

  3. Al revisar el siguiente diseño inicial (figura 2), se decidió realizar un
     cambio para evitar lo que se consideraba un mal olor. El diseño modificado
     se muestra en la figura 3. Indique qué tipo de cambio se realizó y si lo
     considera apropiado. Justifique su respuesta.

  ![ejer3-3](img/p5/ejer3-3.png)

  4. Analice el código que se muestra a continuación. Indique qué defectos
     encuentra y cómo pueden corregirse.


    ```smalltalk
    # imprimirValores
      |totalEdades promedioEdades totalSalarios|
      totalEdades := 0.
      totalSalarios := 0.
      personal do: [ :empleado |
        totalEdades := totalEdades + empleado edad.
        totalSalarios := totalSalarios + empleado salario.
      ].
      promedioEdades := totalEdades / personal size.
      Transcript show: ’Edad promedio: ’, promedioEdad printString ,’ - Total de salarios: ’ , totalSalarios printString.
    ```
