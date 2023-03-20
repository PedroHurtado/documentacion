# Domain Drive Desing

Termino acuñado por Eric Evans

Ventajas de usar domain-driven design:

      Comunicación efectiva entre expertos del dominio y expertos técnicos a través de Ubiquitous Language.

      Foco en el desarrollo de un área dividida del dominio (subdominio) a través de Bounded Context’s.

      El software es más cercano al dominio, y por lo tanto es más cercano al cliente.

      Código bien organizado, permitiendo el testing de las distintas partes del dominio de manera aisladas.
    
      Lógica de negocio reside en un solo lugar, y dividida por contextos.

      Mantenibilidad a largo plazo

## Entidad

    Clase con un identificador único. Es decir dos entidades son iguales si sus identificadores son iguales aunque sus atributos sean distintos.

## Value Object

    Clase inmutable donde dos clases son iguales si todos sus atriburtos son iguales

## Agregado

    Conjunto de clases y value Object que representan una unidad lógica. Por ejemplo en un catálogo de pizzas cada pizza es representada por sus atributos y una colleccion de ingredientes. A su vez la piza es el objeto root.

## Bounded Context

    Cuando los modelos de clases crecen llega un momento que su tamaño es excesivo y uno de los patrones de diseño que se implementa es el de Bounded Context por el cual el modelo se divide en “submodelos” cada uno expecializado en un area

![Descripción de la imagen](https://www.arquitecturajava.com/wp-content/uploads/domaindrivendesign.png)

![Descripción de la imagen](https://www.arquitecturajava.com/wp-content/uploads/liminesBoundedContext.png)

## Eventos del dominio

Nos sirve para comunicar diferentes contextos de dominio. Deben de constar de un identificador único y un timestamp más los atributos necesarios.

Deben formar parte de la transacción y por tanto al comunicar dos bounded context ambos deben de ser transaccionales.

### Outbux pattern

    id          
    aggregatetype
    aggregateid  
    type          
    payload    

## Domain exception

Cualquier regla que no se cumpla en un dominio debe de lanzar una exception. Como buena practica todas deberían heredar de una domain exception base y poseer los siguientes atributos description y code(optional) a efectos de log.

## Interface del repositorio

Interface y no implementación del contrato de repositorio.

```
  public interface Repository{
     Entity get(integer id);
     Remove(Entity);
     Add(Entity);
     Update(Entity);
  }
```

Ejercicios:

-Crear una clase cuenta que al crearse tenga como saldo cero y se puedan hacer operaciones de abono y cargo. El abono incrementará el saldo y los cargos restarán del saldo.

Los importes nunca pueden ser negativos y el saldo de la cuenta nunca puede ser inferior a cero.


-Crear un projecto ShopingCart donde se pueden agregar articulos y eliminar articulos, solo se puede eliminar articulos que están en el carrito. Al agregar un articulo restará del stock del articulo y al quitar el articulo sumará al stock.