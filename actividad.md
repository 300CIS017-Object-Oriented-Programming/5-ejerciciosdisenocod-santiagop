
# Punto 1 :)

### Diseño 1
En la clase espacios pide un tipo, un identificador único, una capacidad máxima, un estado de disponibilidad y una tarifa por hora pero al observar el diagrama no aparece el identificador único. primer error.
el segundo que encuentre es que la flecha de Espacio tiene que ir al contrario,  debe de ir de Reserva a Espacio ya que se complementa y a gestor de reservas faltan mas métodos por asignar.
Hay funcionalidades mal clasificadas, osea que si es __Private__ o __Public__.

### Diseño 2
La clase espacio le faltan atributos requeridos en la descripcion(identificador unico y capacidad) asi como metodos para operar( ¿Esta disponible? o consultar informacion antes de reserva) y lo de la clasificacion de __private__ y __public__.

### Diseño 3
Pasar algunos datos ponerlos privados, falta la funcion liberar reserva( liberarReserva(Espacio) ) y cambiar le flecha de reserva .

## Diagrama de reservas.

    classDiagram
    class Espacio {
        -int idEspacio
        -string +tipo
        -int capacidad
        -bool disponible
        -double tarifa
    }

    class Reserva {
        -int idReserva
        -Espacio* espacio
        +double calcularCosto()
    }

    class GestorReservas {
        +list reservas
        +void consultarDisponibilidad()
        +void realizarReserva(Espacio, int)
        +void cancelarReserva(Reserva)
        +void liberarReserva(Reserva) 
    }
    Espacio "1" -- "1" Reserva : "Usa"
    GestorReservas "1" --> "*" Reserva : "Gestiona"

# Punto 2 :(

### Diagrama de reciclaje

    classDiagram
    direction TB
    class Ciudadano {
        +String id
        +String nombre
        +int telefono
        +int puntos
        +registrarse()
        +entregarMaterial(tipoMaterial, peso)
        +verPuntos()
        +canjearPuntos(puntos)
    }

    class Empleado {
	    +String id
	    +String nombre
	    +registrarEntrega(idCiudadano, tipoMaterial, peso)
	    +calcularPuntos(tipoMaterial, peso)
    }

    class SistemaReciclaje {
	    +registrarCiudadano(id, nombre, telefono)
	    +registrarEntrega(idCiudadano, tipoMaterial, peso)
	    +verPuntos(idCiudadano)
	    +canjearPuntos(idCiudadano, puntos)
    }

    Ciudadano  -->  SistemaReciclaje : utiliza
    Empleado  -->  SistemaReciclaje : trabaja con
    Empleado  -->  Ciudadano : registra entregas


