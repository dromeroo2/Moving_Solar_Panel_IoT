# ☀️ Sistema IoT de Placa Solar Auto-orientable

## Autores
*Alejandro Fuentetaja Simón, Raúl López Llana, Álvaro Radajczyk Sánchez y David Romero Oñoro*

## 📖 Descripción del Proyecto
Este repositorio contiene el proyecto de la asignatura Computación Ubicua. La aplicación y circuitería diseñadas conforman un sistema de seguimiento solar activo que orienta automáticamente un panel fotovoltaico hacia la fuente principal de luz para maximizar la obtención de energía.

El proyecto desarrolla un entorno del Internet de las Cosas (IoT) combinando diseño de hardware (microcontroladores y sensores) con el desarrollo de software a nivel de servidor, base de datos y aplicaciones cliente.


![Funcionamiento del sistema](images/ubicua.gif)


## ⭐ Características Principales
* **Orientación Automática Activa:** Seguimiento dinámico de la luz solar mediante cuatro fotoresistores y motores para asegurar la máxima eficiencia energética.
* **Posición de Seguridad y Mantenimiento:** Opción de reseteo del panel a posición horizontal, facilitando su limpieza manual o protegiendo la estructura frente a condiciones climáticas adversas como fuertes rachas de viento.
* **Arquitectura Escalable IoT:** Sistema basado en el protocolo MQTT para la transmisión de mensajes, permitiendo el control remoto y la agregación de múltiples placas.
* **App Móvil de Control:** Aplicación Android diseñada para supervisar los sensores en tiempo real, recibir notificaciones de alerta (ej. baja exposición de luz o sensores desbalanceados) y gestionar el estado del panel.
* **Dashboard Web de Analítica:** Interfaz web alojada en la nube para visualizar el historial de datos, comparar el rendimiento (voltaje) entre diferentes fechas y analizar estadísticas de generación.

## 🛠️ Tecnologías y Componentes Utilizados

### Capa de Percepción (Hardware)
* **Microcontrolador ESP32 WROOM32:** Placa base con conexión Wi-Fi, programada usando Arduino IDE y configurada para ejecutar tareas en paralelo (multinúcleo) para no interrumpir la conectividad.
* **Sensores:** Fotoresistores (LDR) para medir la luz en diferentes ejes, panel solar de medición y pulsadores para los límites de giro.
* **Actuadores:** Servomotor (para la inclinación vertical) y motor paso a paso (para la rotación horizontal de la base).

### Capa de Transporte y Procesado (Backend)
* **Comunicaciones MQTT:** Broker en la nube EMQX para la telemetría bidireccional entre las placas y el servidor.
* **Base de Datos MySQL:** Base de datos relacional para el registro y almacenamiento histórico de voltaje y lecturas de sensores.
* **Servidor Apache Tomcat:** Motor que sirve la plataforma web y procesa las peticiones de las aplicaciones.
* **Amazon Web Services (AWS):** Infraestructura cloud empleando instancias virtuales (EC2) y servicios de bases de datos relacionales (RDS).

### Capa de Aplicación (Frontend)
* **Aplicación Android:** Programada nativamente con Android Studio, incluye un simulador de datos integrado.
* **Aplicación Web:** Creada con JSP, HTML, CSS y JS, consumiendo datos directamente de la base de datos para la generación de gráficas visuales.

## 🗂️ Arquitectura del Sistema
El proyecto está estructurado lógicamente en cuatro capas funcionales fundamentales para un entorno ubicuo:
* **Capa de Percepción:** Recolección de datos del mundo físico a través de sensores y manipulación del entorno vía motores.
* **Capa de Transporte:** Transmisión de datos inalámbrica desde el ESP32 hacia internet empleando el protocolo MQTT.
* **Capa de Procesado:** Lógica de negocio, ingesta de datos y consultas almacenadas centralmente en AWS (Broker + MySQL + Tomcat).
* **Capa de Aplicación:** Muestra de información estructurada y tabulada a los usuarios mediante dispositivos móviles y navegadores web.

![Arquitectura](images/Arqui con circuito.gif)
