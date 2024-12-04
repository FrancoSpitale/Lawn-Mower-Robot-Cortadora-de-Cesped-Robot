Descripción del Código
Este código es un programa para el control de un robot cortacésped autónomo, diseñado para realizar tareas de corte de césped, detección de obstáculos, monitoreo de batería, y comunicación con una aplicación mediante Bluetooth. Está implementado para un microcontrolador PIC16F886 y utiliza varias funciones avanzadas para garantizar un funcionamiento autónomo y seguro.

Características Principales
Control de Motores:

Maneja cuatro pines (in1, in2, in3, in4) para el control de motores de ruedas mediante un puente H.
Funciones específicas para manejar las ruedas hacia adelante, atrás, izquierda y derecha.
Cuchilla:

Controla la cuchilla de corte con protección contra sobrecarga.
Apaga la cuchilla automáticamente si detecta un atasco o si se levanta el robot.
Sensores:

Ultrasónico: Detecta obstáculos y mide distancias.
Magnético: Detecta el campo perimetral para evitar que el robot salga de la zona de corte.
DHT11: Mide la temperatura y la humedad, ajustando su comportamiento según estas condiciones.
Batería:

Monitorea la carga de la batería.
Regresa a la base de carga automáticamente cuando la batería está baja.
Detección de Obstáculos:

Identifica y evade obstáculos en el camino.
Realiza maniobras evasivas (retroceso, giro) para sortear el obstáculo.
Bluetooth:

Permite la interacción del robot con una aplicación móvil para control remoto y monitoreo de parámetros como batería, sensores y estado de los motores.
Recibe comandos para manejar manualmente el robot o activar/desactivar funciones.
Programación del Robot:

Configuración de días de operación a través de un pulsador.
Se programa el robot para operar en días específicos de la semana.
Calendario y Ciclo de Trabajo:

El robot funciona basado en un calendario semanal.
Realiza tareas de corte en días asignados o permanece en la base en otros días.
Funciones Importantes
Conversion():

Convierte las señales analógicas de los sensores en valores digitales.
Obstaculos():

Detecta obstáculos frontales y ejecuta maniobras evasivas.
Promedio_traccion():

Calcula el promedio de la corriente consumida por los motores para monitorear su desempeño.
Pwm_cuchilla():

Controla el movimiento de la cuchilla y la detiene si detecta un atasco.
Retorno():

Permite al robot regresar a la base de carga siguiendo el cable magnético perimetral.
Humedad_Temperatura():

Lee los datos del sensor DHT11 y ajusta el comportamiento del robot según las condiciones ambientales.
Bateria():

Monitorea el nivel de carga de la batería y activa la bandera de retorno a la base si la carga es baja.
Pulso():

Configura manualmente la programación del robot mediante un pulsador.
Programa():

Ejecuta el ciclo de trabajo del robot basado en la programación configurada.
bluetooth():

Implementa la comunicación Bluetooth para recibir comandos y enviar datos al usuario.
Lógica de Operación
Inicio:

Configura los pines del microcontrolador.
Habilita las interrupciones para manejar el temporizador, el ADC, y la recepción de datos por Bluetooth.
Ciclo Principal:

Monitorea continuamente el estado de la batería y los sensores.
Si es un día asignado para cortar:
Detecta obstáculos y realiza maniobras evasivas.
Controla el movimiento de la cuchilla y las ruedas.
Si la batería está baja o no es un día asignado, retorna a la base.
Modo Manual:

Permite al usuario controlar el robot mediante comandos Bluetooth.
Protección:

Apaga automáticamente los motores y la cuchilla si se detectan condiciones peligrosas (como levantar el robot o atasco de la cuchilla).
Interacción con el Usuario
Bluetooth:

Comandos Recibidos:
1 a 5: Configura la programación del robot.
u/l/r/d: Mueve el robot hacia adelante, izquierda, derecha o atrás.
c: Activa la cuchilla.
C: Detiene la cuchilla.
R: Retorna a la base.
Datos Enviados:
Estado del robot.
Valores de batería, temperatura, humedad, y sensores.
Pulsador:

Configura el ciclo de trabajo mediante una secuencia de pulsaciones.
Buzzer:

Emite sonidos para confirmar acciones o alertar sobre eventos.
