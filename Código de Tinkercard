// Definición de pines para los LEDs
const int ledVerdePin = 7;
const int ledRojoPin = 12;
const int ledAmarilloPin = 13;

// Variables para el estado de los LEDs
bool estadoVerde = false;
bool estadoRojo = false;
bool estadoAmarillo = false;

void setup() {
  // Configuración de pines como salida
  pinMode(ledVerdePin, OUTPUT);
  pinMode(ledRojoPin, OUTPUT);
  pinMode(ledAmarilloPin, OUTPUT);
  
  // Inicialización del Serial Monitor
  Serial.begin(9600);
  
  // Mensaje inicial en el Serial Monitor
  Serial.println("Control de luces de vivienda:");
  Serial.println("1: Encender luz verde");
  Serial.println("2: Apagar luz verde");
  Serial.println("3: Encender luz roja");
  Serial.println("4: Apagar luz roja");
  Serial.println("5: Encender luz amarilla");
  Serial.println("6: Apagar luz amarilla");
  Serial.println("7: Encender todas las luces");
  Serial.println("8: Apagar todas las luces");
  Serial.println("9: Modo intermitente");
}

void loop() {
  if (Serial.available()) {
    char opcion = Serial.read(); // Lee la opción ingresada en el Serial Monitor

    switch (opcion) {
      case '1':
        controlarLuz(ledVerdePin, true, estadoVerde);
        break;
      case '2':
        controlarLuz(ledVerdePin, false, estadoVerde);
        break;
      case '3':
        controlarLuz(ledRojoPin, true, estadoRojo);
        break;
      case '4':
        controlarLuz(ledRojoPin, false, estadoRojo);
        break;
      case '5':
        controlarLuz(ledAmarilloPin, true, estadoAmarillo);
        break;
      case '6':
        controlarLuz(ledAmarilloPin, false, estadoAmarillo);
        break;
      case '7':
        controlarTodasLasLuces(true);
        break;
      case '8':
        controlarTodasLasLuces(false);
        break;
      case '9':
        modoIntermitente();
        break;
      default:
        Serial.println("Opción no válida");
        break;
    }
  }
}

// Función para controlar una luz individual
void controlarLuz(int pin, bool estado, bool &estadoLuz) {
  digitalWrite(pin, estado ? HIGH : LOW);
  estadoLuz = estado;
  Serial.print("Luz ");
  Serial.print(pin);
  Serial.println(estado ? " encendida" : " apagada");
}

// Función para encender o apagar todas las luces
void controlarTodasLasLuces(bool estado) {
  controlarLuz(ledVerdePin, estado, estadoVerde);
  controlarLuz(ledRojoPin, estado, estadoRojo);
  controlarLuz(ledAmarilloPin, estado, estadoAmarillo);
  Serial.println(estado ? "Todas las luces encendidas" : "Todas las luces apagadas");
}

// Función para poner las luces en modo intermitente
void modoIntermitente() {
  Serial.println("Modo intermitente activado");
  for (int i = 0; i < 10; i++) {  // Intermitente durante 10 ciclos
    controlarTodasLasLuces(true);
    delay(500);
    controlarTodasLasLuces(false);
    delay(500);
  }
}
