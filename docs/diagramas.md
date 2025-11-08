# Diagramas

En esta sección se presenta el diagrama de clases del sistema, elaborado con Mermaid.

El diagrama muestra la estructura de las clases principales, sus atributos, métodos y relaciones.
Se puede observar cómo Silla y Escritorio heredan de la clase base Mueble, lo que permite reutilizar código y mantener una jerarquía clara dentro del modelo de objetos.

Además, la clase Muebleria se relaciona con varias instancias de Mueble (asociación de tipo “uno a muchos”), y gestiona las interacciones con objetos de tipo Cliente.

Este diagrama es útil para comprender la arquitectura del sistema antes de revisar el código fuente, facilitando la documentación y comunicación técnica del proyecto.

## Diagrama de Clases

```mermaid
classDiagram
    class Mueble {
        -nombre: str
        -tipo: str
        -precio: float
        -stock: int
        +__init__(nombre, tipo, precio, stock)
        +__str__() str
        +vender(cantidad: int) float
    }

    class Silla {
        -con_respaldo: bool
        +__init__(nombre, precio, stock, con_respaldo=True)
        +__str__() str
    }

    class Escritorio {
        -material: str
        -con_cajones: bool
        +__init__(nombre, precio, stock, material="madera", con_cajones=True)
        +__str__() str
    }

    class Cliente {
        -nombre: str
        -telefono: str
        +__init__(nombre, telefono)
        +__str__() str
    }

    class Muebleria {
        -nombre: str
        -inventario: list
        -ventas_totales: float
        +__init__(nombre)
        +agregar_mueble(mueble: Mueble)
        +mostrar_inventario()
        +vender_mueble(nombre_mueble: str, cantidad: int, cliente: Cliente)
        +mostrar_ventas_totales()
    }

    %% Relaciones
    Silla --|> Mueble
    Escritorio --|> Mueble
    Muebleria "1" o-- "many" Mueble : contiene
    Muebleria "1" o-- "many" Cliente : realiza ventas

```

## Diagramas de Secuencia

```mermaid
sequenceDiagram
    Alice->>+John: Hello John, how are you?
    Alice->>+John: John, can you hear me?
    John-->>-Alice: Hi Alice, I can hear you!
    John-->>-Alice: I feel great!
```

## Diagrama Entidad - Relación

```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ ORDER_ITEM : contains
    PRODUCT ||--o{ ORDER_ITEM : includes
    CUSTOMER {
        string id
        string name
        string email
    }
    ORDER {
        string id
        date orderDate
        string status
    }
    PRODUCT {
        string id
        string name
        float price
    }
    ORDER_ITEM {
        int quantity
        float price
    }
```
