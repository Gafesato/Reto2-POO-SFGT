# Reto 2 de la clase Programación Orientada a Objetos
---
## Contenidos

1. [Descripción](#descripción)
2. [Boceto e ideas de las clases](#boceto)
3. [Código UML en Mermaid](#código-uml-en-mermaid)
4. [Diagrama UML obtenido](#diagrama-uml-obtenido)

---

## Descripción

El sistema modela un mercado financiero con clases para Bolsa, Participantes (Trader, Broker, Banco), Divisas, y Operaciones. Este modelo es útil para representar la dinámica de trading y la estructura de los actores involucrados.

---

## Boceto

Comencé diciendo que solo incluiría el Mercado Forex como un tipo de Mercado, pero terminé generalizando, ya que crear una estructura tan jerarquizada no conviene por la extensión del ejercicio.

[Descargar el PDF original](./UML.pdf)

---

## Código UML en Mermaid

Ahora presento el código en Mermaid como texto:

```bash
classDiagram
    class Mercado {
        +Bolsa bolsa
        +Divisa divisa
        +Participante participantes
    }
    class Bolsa {
        +String ubicacion
        +String horario
        +Divisa divisa_principal
        +int volumen_transacciones
        +abrir_bolsa()
        +cerrar_bolsa()
    }
    class Participante {
        +String nombre
        +Int sujeto_id
        +tomar_operacion(Orden)
        +cerrar_operacion(orden_id)
    }
    class Trader {
        +Int balance
        +Broker broker
        +mostrar_balance() float
    }
    class Broker {
        +String pais
        +eliminar_trader(Trader)
        +enviar_orden(Trader)
    }
    class Banco {
        +String pais
        +regular_divisa(Divisa)
    }
    class Divisa {
        +String par
        +String divisa_base
        +String divisa_cotizada
        +Float valor_actual
    }
    class Orden{
        +Int orden_id
        +String tipo
        +Float precio_entrada
        +Float take_profit
        +Float stop_loss
        +Float volumen_operado
    }
    
    %% Relaciones de composición
    Mercado --> Bolsa : contiene
    Mercado --> Divisa : contiene
    Mercado --> Participante : contiene
    Bolsa --> Divisa : tiene

    %% Relaciones de herencia
    Participante <|-- Trader : es un
    Participante <|-- Broker : es un
    Participante <|-- Banco : es un

    %% Relaciones adicionales
    Trader --> Broker : usa
    Broker --> Orden : envía
    Banco --> Divisa : regula
    Participante --> Orden : opera
```
---

## Diagrama UML obtenido

```mermaid
---
config:
  theme: dark
---
classDiagram
    class Mercado {
        +Bolsa bolsa
        +Divisa divisa
        +Participante participantes
    }
    class Bolsa {
        +String ubicacion
        +String horario
        +Divisa divisa_principal
        +int volumen_transacciones
        +abrir_bolsa()
        +cerrar_bolsa()
    }
    class Participante {
        +String nombre
        +Int sujeto_id
        +tomar_operacion(Orden)
        +cerrar_operacion(orden_id)
    }
    class Trader {
        +Int balance
        +Broker broker
        +mostrar_balance() float
    }
    class Broker {
        +String pais
        +eliminar_trader(Trader)
        +enviar_orden(Trader)
    }
    class Banco {
        +String pais
        +regular_divisa(Divisa)
    }
    class Divisa {
        +String par
        +String divisa_base
        +String divisa_cotizada
        +Float valor_actual
    }
    class Orden{
        +Int orden_id
        +String tipo
        +Float precio_entrada
        +Float take_profit
        +Float stop_loss
        +Float volumen_operado
    }
    
    %% Relaciones de composición
    Mercado --> Bolsa : contiene
    Mercado --> Divisa : contiene
    Mercado --> Participante : contiene
    Bolsa --> Divisa : tiene

    %% Relaciones de herencia
    Participante <|-- Trader : es un
    Participante <|-- Broker : es un
    Participante <|-- Banco : es un

    %% Relaciones adicionales
    Trader --> Broker : usa
    Broker --> Orden : envía
    Banco --> Divisa : regula
    Participante --> Orden : opera
