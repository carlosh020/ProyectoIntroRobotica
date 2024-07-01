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
