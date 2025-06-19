# APP Detección de Conductores

Aplicación Android capaz de detectar si el conductor de un vehículo se está quedando dormido y emitir alertas para despertarlo, utilizando visión por computadora y un modelo de inteligencia artificial.

## Tabla de Contenidos
- [Descripción General](#descripción-general)
- [Características](#características)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Requisitos](#requisitos)
- [Instalación y Ejecución](#instalación-y-ejecución)
- [Funcionamiento](#funcionamiento)
- [Modelo de IA](#modelo-de-ia)
- [Integración con Firebase](#integración-con-firebase)
- [Notas de Seguridad y Privacidad](#notas-de-seguridad-y-privacidad)
- [Autores](#autores)
- [Referencias](#referencias)
- [Licencia](#licencia)

---

## Descripción General
Esta app utiliza la cámara frontal del dispositivo para analizar el rostro del conductor y detectar signos de somnolencia (ojos cerrados). Si se detecta que el conductor se está quedando dormido, la app emite una alerta sonora para despertarlo.

## Características
- Registro y autenticación de usuarios.
- Encuesta de salud para personalizar la experiencia.
- Detección en tiempo real de ojos abiertos/cerrados usando un modelo TensorFlow Lite.
- Alerta sonora automática si se detecta somnolencia.
- Historial de resultados de análisis.
- Integración con Firebase para gestión de usuarios.

## Estructura del Proyecto
```
MyApp2-master/
  ├── app/
  │   ├── src/
  │   │   ├── main/
  │   │   │   ├── java/com/arcedios/myapp2/
  │   │   │   │   ├── Model/         # Lógica de IA y Firebase
  │   │   │   │   ├── ModelView/     # Modelo de datos de usuario
  │   │   │   │   └── View/          # Actividades principales (UI)
  │   │   │   ├── res/               # Recursos gráficos y layouts
  │   │   │   ├── ml/model.tflite    # Modelo de IA
  │   │   │   └── AndroidManifest.xml
  │   ├── build.gradle.kts
  │   └── ...
  └── README.md
```

## Requisitos
- Android Studio (recomendado: versión Electric Eel o superior)
- SDK de Android 30+
- Dispositivo o emulador con cámara frontal
- Conexión a internet para autenticación y Firebase

## Instalación y Ejecución
1. Clona este repositorio y abre el proyecto en Android Studio.
2. Asegúrate de tener el archivo `google-services.json` en `app/` para la integración con Firebase.
3. Sincroniza las dependencias Gradle.
4. Conecta un dispositivo físico o inicia un emulador con cámara.
5. Compila y ejecuta la app.

## Funcionamiento
### Flujo de Usuario
1. **SplashScreen:** Verifica si hay usuarios registrados en Firebase. Si no, redirige a registro.
2. **Registro:** El usuario ingresa nombre, cédula, edad y responde una encuesta de salud. Los datos se almacenan en Firebase.
3. **Login:** El usuario ingresa nombre y cédula. Se valida contra Firebase.
4. **Servicios:** Se activa la cámara frontal y el modelo de IA analiza el rostro cada 2 segundos. Si se detectan ojos cerrados, se emite una alerta sonora.

### Detección de Somnolencia
- El modelo `model.tflite` clasifica la imagen en tres categorías: `Ojos abiertos`, `Ojos cerrados`, `No hay nadie`.
- Si la probabilidad de ojos cerrados supera un umbral, se activa una alerta.

## Modelo de IA
- El modelo está basado en TensorFlow Lite y espera imágenes de 224x224 píxeles.
- La clase `Classifier` gestiona la carga y predicción del modelo.

## Integración con Firebase
- La clase `TodoFirebase` gestiona el registro y autenticación de usuarios en la base de datos en tiempo real de Firebase.
- Los datos de usuario se almacenan bajo el nodo `Usuarios`.

## Dependencias Principales
- [TensorFlow Lite](https://www.tensorflow.org/lite)
- [Firebase Realtime Database](https://firebase.google.com/products/realtime-database)
- [AndroidX CameraX](https://developer.android.com/training/camerax)
- [JavaCV](https://github.com/bytedeco/javacv)

## Notas de Seguridad y Privacidad
- Las imágenes capturadas solo se procesan localmente y no se almacenan ni envían a servidores externos.
- Los datos personales se almacenan en Firebase bajo las políticas de privacidad de Google.

## Autores
- Universidad Nacional de Colombia
- Proyecto de POO

---

Si tienes dudas o sugerencias, por favor abre un issue o contacta a los autores.
