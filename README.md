# Proyecto-Final-Sistemas-de-Vision-Industrial

Este proyecto utiliza Python y OpenCV para reconocer gestos de la mano a través de una cámara web y controlar LEDs conectados a una placa Arduino en tiempo real.

---

## Características

- *Reconocimiento de Gestos*:
  - Detecta el número de dedos levantados (0, 1, 2).
  - Identifica movimientos de "saludo" (waving).
- *Control de LEDs*:
  - Enciende o apaga LEDs en Arduino según el gesto detectado.
- *Calibración Automática*:
  - Adapta el sistema a diferentes condiciones de iluminación y tonos de piel.
- *Retroalimentación Visual*:
  - Muestra el estado del sistema y gestos detectados en el video en vivo.

---

## Requisitos

### Hardware
- Una *cámara web*.
- Una placa *Arduino* con LEDs conectados.
- Un cable USB para conectar Arduino a la PC.

### Software
- *Python 3.x*.
- *Arduino IDE* (para cargar un sketch en Arduino).

## Cómo Ejecutar

1. *Configura tu Arduino*:
   - Conecta tu placa Arduino y carga el siguiente código usando el Arduino IDE:
     cpp
     void setup() {
       Serial.begin(9600);
       pinMode(2, OUTPUT); // LED 1
       pinMode(3, OUTPUT); // LED 2
     }

     void loop() {
       if (Serial.available()) {
         char command = Serial.read();
         if (command == '0') {
           digitalWrite(2, LOW);
           digitalWrite(3, LOW);
         } else if (command == '1') {
           digitalWrite(2, HIGH);
           digitalWrite(3, LOW);
         } else if (command == '2') {
           digitalWrite(2, HIGH);
           digitalWrite(3, HIGH);
         }
       }
     }
     

2. *Prepara tu entorno en Python*:
   - Asegúrate de tener las siguientes librerías instaladas:
     bash
     pip install numpy opencv-python pyserial
     

3. *Configura el puerto serial*:
   - Abre el archivo Python del proyecto y verifica que el puerto serial (COM4 por defecto) coincida con el que utiliza tu Arduino. Si no estás seguro, verifica en el Administrador de Dispositivos o Arduino IDE.

4. *Ejecuta el programa*:
   - Inicia el programa desde tu terminal o entorno de desarrollo ejecutando el siguiente comando:
     bash
     python hand_gesture_arduino.py
     

5. *Prueba los gestos*:
   - Coloca tu mano frente a la cámara y realiza los siguientes gestos para controlar los LEDs:
     - *0 dedos*: Apaga todos los LEDs.
     - *1 dedo*: Enciende un LED.
     - *2 dedos*: Enciende dos LEDs.
     - *Movimiento de la mano*: Detecta un "saludo".

6. *Finaliza el programa*:
   - Para salir del programa, presiona la tecla *X* en la ventana de la cámara.


### Librerías de Python
Instala las dependencias con el siguiente comando:
```bash
pip install numpy opencv-python pyserial
