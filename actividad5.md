## Tipos de Kernel y sus Diferencias

1. **Monolítico**:
   - **Descripción**: Todos los servicios del sistema operativo (gestión de procesos, memoria, controladores de dispositivos, etc.) se ejecutan en el espacio de kernel.
   - **Ventajas**: Alto rendimiento debido a la reducción de la sobrecarga de contexto.
   - **Desventajas**: Mayor riesgo de fallos, ya que un error en un módulo puede comprometer todo el sistema.

2. **Microkernel**:
   - **Descripción**: Solo las funciones esenciales, como la comunicación entre procesos y la gestión básica de hardware, se ejecutan en el espacio de kernel. El resto de servicios se ejecutan en el espacio de usuario.
   - **Ventajas**: Mayor estabilidad y seguridad; los fallos en los servicios no afectan al kernel.
   - **Desventajas**: Potencial menor rendimiento debido a la sobrecarga de comunicación entre procesos.

3. **Exokernel**:
   - **Descripción**: Se minimiza la funcionalidad del kernel, permitiendo que las aplicaciones gestionen directamente el hardware a través de una capa de abstracción muy delgada.
   - **Ventajas**: Gran flexibilidad y potencial para optimizaciones a nivel de aplicación.
   - **Desventajas**: Complejidad en el desarrollo de aplicaciones, ya que deben gestionar directamente muchos aspectos del hardware.

4. **Nanokernel**:
   - **Descripción**: Similar al microkernel pero más simplificado; su función principal es proporcionar una base para la ejecución de múltiples kernels sobre un mismo hardware.
   - **Ventajas**: Alta portabilidad y flexibilidad para sistemas heterogéneos.
   - **Desventajas**: Puede ser limitado en funcionalidad y no tan común en implementaciones generales.

5. **Kernel Híbrido**:
   - **Descripción**: Combina elementos de microkernel y kernel monolítico. Servicios básicos se ejecutan en modo kernel, mientras que otros servicios se ejecutan en espacio de usuario.
   - **Ventajas**: Balance entre rendimiento y modularidad.
   - **Desventajas**: Puede ser complejo de implementar y mantener.

## User Mode vs Kernel Mode

- **User Mode**:
  - **Descripción**: Es el modo de operación en el que se ejecutan las aplicaciones de usuario. Las aplicaciones tienen acceso limitado al hardware y deben usar llamadas al sistema para interactuar con él.
  - **Limitaciones**: No pueden ejecutar instrucciones privilegiadas directamente y están sujetas a restricciones para evitar que afecten la estabilidad del sistema.

- **Kernel Mode**:
  - **Descripción**: Es el modo de operación con acceso completo al hardware y a las instrucciones privilegiadas del procesador. El kernel y ciertos drivers se ejecutan en este modo.
  - **Capacidades**: Permite la ejecución de cualquier instrucción y acceso a todo el hardware, por lo que puede gestionar todos los recursos del sistema.

## Interrupciones vs Traps

- **Interrupciones**:
  - **Descripción**: Son señales enviadas por hardware o software para interrumpir la ejecución del CPU y solicitar la atención del sistema operativo. Las interrupciones pueden ser generadas por eventos como la finalización de una operación de E/S.
  - **Tipos**: 
    - *Interrupciones de hardware*: Originadas por dispositivos físicos (teclado, disco duro, etc.).
    - *Interrupciones de software*: Generadas por el software, como una solicitud de servicio (system call).
  - **Manejo**: El procesador guarda su estado actual y transfiere el control al manejador de interrupciones designado por el sistema operativo.

- **Traps**:
  - **Descripción**: Son una clase especial de interrupciones generadas intencionadamente por el software para ejecutar una rutina del sistema operativo, como una llamada al sistema (system call) o para manejar errores como división por cero.
  - **Tipos**:
    - *System call*: Un trap generado por un programa para solicitar un servicio del sistema operativo.
    - *Fault*: Un trap generado por errores en el código, como una operación ilegal o una referencia a memoria inválida.
  - **Manejo**: Similar a las interrupciones, el control se transfiere al kernel para manejar la situación específica.
