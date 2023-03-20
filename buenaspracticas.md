Buenas prácticas
================

Sobre el código fuente
----------------------

- Principios solid
    - Single Responsability Principle
    - Open-Closed Principle
    - Liskov Substitution Principle
    - Interface Segregation Principle
    - Dependecy Inversion Principle
  
El primero y el último de los principios SOLID son esenciales para generar código que sea fácil de testear.

- Query & Command functions

Hay que intentar evitar por todos los medios que nuestras funciones sean al mismo tiempo query y command, ya que aumentarán la complejidad de los tests.

Además, si una función es a la vez de tipo query y de tipo command, está incumpliendo el principio de Single Responsability.

- Hacer return de más de un tipo de dato

Una función que devuelva distintas cosas dependiendo de una condición interna complica el testeo. Por ejemplo, que devuelva un array de objetos si todo va bien, pero devuela un string con un mensaje de error si hay algún problema.

El return debe ser homegéneo para todos los casos. Si se producen errores, se deben tratar con excepciones.