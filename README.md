# Prueba de concepto: Actualización Dinámica y Persistente de Datos en el Panel Frontal en LabVIEW - Controles Path

## 📄 Descripción del proyecto

Esta aplicación fue desarrollada como una **prueba de concepto** en **LabVIEW**, con el objetivo de abordar una necesidad frecuente en aplicaciones reales: la **persistencia de datos de configuración**.

En muchos desarrollos, es común que ciertos valores deban ser modificados por el usuario durante la ejecución (parámetros de funcionamiento, ajustes, configuraciones, datos personalizados, etc.). Sin embargo, es fundamental que estos valores **no se pierdan al cerrar la aplicación**, sino que se conserven y estén disponibles la próxima vez que se ejecute.

Esta prueba de concepto implementa una solución sencilla y eficaz para este propósito: los datos de configuración se almacenan automáticamente en un archivo **`.ini`**, permitiendo que la aplicación los recupere al iniciarse.

De esta manera, cualquier modificación realizada por el usuario queda registrada de forma permanente, incluso después de cerrar y volver a abrir la aplicación.

Además, el desarrollo está estructurado en base al patrón de diseño **QMH (Queued Message Handler)**, ampliamente utilizado en aplicaciones escalables y modulares en LabVIEW.

## 💡 Objetivo

Demostrar cómo se puede implementar un mecanismo básico de **guardado y recuperación automática de configuraciones** en una aplicación LabVIEW, utilizando archivos `.ini` como medio de almacenamiento persistente.

Este ejemplo puede servir como base para desarrollos más complejos que requieran conservar configuraciones entre sesiones.

## 📂 Estructura del archivo `.ini`

El archivo `.ini` generado contiene los valores de configuración organizados en secciones y claves, con el formato típico de este tipo de archivos:

```ini
[REDRAT]
xml_path = "C:\\Users\\Taboada.r248\\Documents\\LabVIEW Projects\\PMT Project\\PMT-Get-Reference-Measurements\\redrat\\xml\\TCL_signatures_DB_v1.xml"

[CAPTURES]
folder_path = "C:\\Users\\Taboada.r248\\Documents\\AdobeStockPhotos"
```

## ▶️ Comportamiento de la aplicación

- **Al iniciar la aplicación:**
  - Se carga el archivo `.ini` (si existe) y se actualizan los valores de configuración.
  - Si el archivo no existe, se emitirá el error correspondiente.

- **Durante la ejecución:**
  - El usuario puede modificar los valores de las llaves desde el Front Panel (FP).
  - También puede editar directamente el archivo `.ini` (manteniendo el número de sectores y llaves), y actualizar los cambios en el FP utilizando el botón **`Update`**.

- **Al cerrar la aplicación:**
  - Los valores actuales se guardan automáticamente en el archivo `.ini` para ser reutilizados en la siguiente ejecución.

---

## 📌 Nota

Este proyecto tiene únicamente fines demostrativos y no está orientado al uso productivo. Su finalidad es ilustrar el concepto de **persistencia de configuraciones** en aplicaciones LabVIEW, y cómo estas configuraciones pueden mantenerse y actualizarse durante el ciclo de vida de la aplicación.

Además, sirve como ejemplo básico del uso del patrón de diseño **QMH (Queued Message Handler)** en el desarrollo de aplicaciones LabVIEW estructuradas, modulares y mantenibles.

![imagen]

![Diagrama de flujo](https://github.com/user-attachments/assets/0ab7f27b-417b-418b-bea2-c7f72bc8565f)

### 📌 Historial de versiones

#### 🟢 Versión 1.0
- Se mejora la implementación del manejo de persistencia de datos en el Front Panel.
- Se reemplazaron los nodos de propiedad (`Property Node – Value`) por los nodos `Set Control Values by Index` y `Get Control Values by Index`.
- Este cambio favorece la escalabilidad, limpieza y mantenibilidad del código, especialmente en aplicaciones con múltiples controles.
- El nuevo enfoque requiere una lógica algo más elaborada para gestionar la lectura y escritura de archivos `.ini`, lo cual demandó mayor dedicación en el diseño del módulo correspondiente. No fue complejo, pero sí requirió cierto grado de astucia.
