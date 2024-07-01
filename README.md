# Informe del Proyecto: Robot Seguidor de Líneas con Arduino

  Descripción del Proyecto y Problema a Resolver
El presente proyecto tiene como objetivo diseñar y construir un robot seguidor de líneas utilizando una placa Arduino, dos motores DC y un sensor de reflectancia. El robot debe ser capaz de seguir una línea negra sobre una superficie clara de manera autónoma. La resolución de este problema implica la integración de componentes electrónicos y la programación de un sistema de control eficiente.

La principal motivación detrás del proyecto es crear un robot que pueda moverse de manera precisa siguiendo un camino predeterminado. Este tipo de robots tienen aplicaciones en diversas áreas, como en sistemas de transporte automatizados, robots de limpieza y en competiciones de robótica educativa. El desafío es lograr que el robot interprete correctamente las señales de los sensores y ajuste su trayectoria en tiempo real para seguir la línea con precisión.

  Componentes Utilizados
- Arduino Uno: Microcontrolador para controlar el robot.
- Motores DC: Dos motores para el movimiento del robot.
- Puente H (L298N): Módulo para controlar la dirección y velocidad de los motores.
- Sensor de Reflectancia QTR-8A: Sensor con 8 LEDs infrarrojos y fototransistores que detectan la línea.
- Componentes adicionales: Resistencias, cables, y una estructura para el robot.

  Conexiones
Motores: Conectados a los pines digitales del Arduino a través del puente H.
Motor 1: Pines 2 y 5 (dirección), Pin 3 (velocidad - PWM)
Motor 2: Pines 8 y 9 (dirección), Pin 10 (velocidad - PWM)

  Código del Proyecto
El código adjunto muestra la implementación en Arduino para controlar el robot seguidor de líneas. Incluye la configuración de los pines, la calibración de los sensores, y la lógica para seguir la línea.

  Resolución del Problema
El problema principal de seguir una línea con precisión se resolvió mediante una serie de pasos:

1. Calibración de Sensores: Calibrar los sensores de reflectancia para obtener valores precisos de la línea negra y la superficie clara. Durante la calibración, se capturan los valores mínimos y máximos de los sensores mientras el robot usa sus motores para girar y pasar encima de la linea negra.
2. Promedios Ponderados: Utilizar promedios ponderados de los sensores para determinar la posición de la línea. Esto permite una mayor precisión al determinar la posición de la línea y hacer ajustes a la dirección del robot.
3. Control de Motores: Implementar una lógica de control para ajustar la velocidad y dirección de los motores basada en la lectura de los sensores. Si el sensor central detecta la línea, el robot avanza; si los sensores laterales detectan la línea, el robot gira en la dirección opuesta.
4. Pruebas y Ajustes: Realizar múltiples pruebas en la pista con diferentes configuraciones de velocidad para ajustar y optimizar el comportamiento del robot.

  Modificación del Código para Seguir una Ruta Cuadrada
Para que el robot siga una ruta cuadrada, es necesario ajustar la lógica de movimiento para que pueda reconocer y tomar decisiones en las esquinas. Esto implica detectar cuándo el robot llega a una esquina y luego girar en la dirección adecuada para continuar siguiendo la línea. Aquí hay un ejemplo de cómo modificar el código para lograr esto:

1. Agregar Variables de Estado: Necesitamos agregar variables para rastrear el estado actual del robot, como si está en una línea recta, girando o en una esquina.
2. Actualizar la Lógica de Movimiento: Modificar la lógica del loop para incluir la detección de esquinas y realizar los giros correspondientes.

Nuestra solucion en el codigo utilizado en clase la realizamos obligando al robot a que girase cuando se detecta la linea por el sensor central y uno de algun lado, izquierda o derecha, pero no hemos sido capaces de asegurar su funcionamiento sin fallos. Por eso en este informe se presenta una solucion que deberia funcionar con mas eficiencia.

switch (currentState) {
    // case FOLLOW_LINE:
      if (ScBlack && !SiBlack && !SdBlack) {
        forward(MCqueen1);
      } else if (SiBlack && !SdBlack) {
        turnRight(0, MCqueen2);
      } else if (!SiBlack && SdBlack) {
        turnLeft(MCqueen1, 0);
      } else if (SiBlack && SdBlack) {
        Stop();
        currentState = TURN_CORNER;
      }
      break;

    case TURN_CORNER:
      // Gira el robot hasta que solo el sensor central detecte la línea
      if (!ScBlack && (SiBlack || SdBlack)) {
        turnLeft(MCqueen1, 0);
      } else if (ScBlack && !SiBlack && !SdBlack) {
        forward(MCqueen1);
        currentState = FOLLOW_LINE;
      }
      break;
  }

