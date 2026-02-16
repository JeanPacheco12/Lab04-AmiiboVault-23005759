# Amiibo Vault 

Proyecto de **Módulo 3: Arquitectura y Persistencia**. Esta aplicación demuestra una arquitectura **Offline-First** robusta utilizando las mejores prácticas modernas de desarrollo Android.

## Descripción del Proyecto

Amiibo Vault es una aplicación que permite explorar la colección completa de figuras Amiibo de Nintendo. La app está diseñada para ser resiliente a la falta de conectividad, permitiendo al usuario ver, buscar y explorar su colección incluso sin acceso a internet.

## Funcionalidades Implementadas (Challenge Lab)

Este proyecto incluye la resolución completa del "Challenge Lab", dividido en dos partes fundamentales:

### Parte 1: Graceful Offline Mode (Modo Sin Conexión Elegante)
Se mejoró la experiencia de usuario (UX) para manejar errores de red sin bloquear la interfaz.
- **Persistencia de Caché:** Si la actualización de red falla, la app mantiene visibles los datos almacenados localmente en lugar de mostrar una pantalla de error vacía.
- **Manejo de Errores No Bloqueante:** Implementación de un `Snackbar` con opción de "Reintentar" para notificar problemas de conexión sin interrumpir la navegación.
- **UiState Híbrido:** El estado de la UI (`AmiiboUiState.Error`) fue modificado para transportar tanto el mensaje de error como los datos en caché (`cachedAmiibos`).

### Parte 2: Local Search (Búsqueda Local Reactiva)
Implementación de un buscador en tiempo real que filtra directamente sobre la base de datos local.
- **Búsqueda SQL:** Consulta en Room utilizando el operador `LIKE` para filtrar por nombre de manera eficiente.
- **Reactive Flow Switching:** Uso del operador `flatMapLatest` en el ViewModel para alternar dinámicamente entre la lista completa y los resultados de búsqueda según el usuario escribe.
- **UI de Búsqueda:** `TopAppBar` personalizada con un `OutlinedTextField`, botón de limpieza y actualizaciones en tiempo real.

## Tech Stack & Arquitectura

El proyecto sigue una arquitectura **MVVM (Model-View-ViewModel)** con **Clean Architecture** y el patrón **Repository**.

* **Lenguaje:** Kotlin
* **UI:** Jetpack Compose (Material 3)
* **Inyección de Dependencias:** Koin
* **Base de Datos Local:** Room (SQLite abstraction)
* **Networking:** Retrofit + OkHttp
* **Serialización:** Kotlinx Serialization
* **Carga de Imágenes:** Coil
* **Concurrencia:** Coroutines & Flows (StateFlow, SharedFlow)

## 📂 Estructura de Archivos Clave

* `data/dao/AmiiboDao.kt`: Consultas SQL (`searchAmiibos`, `getAll`).
* `repository/AmiiboRepository.kt`: Lógica de sincronización y fuente de verdad única.
* `ui/viewmodel/AmiiboViewModel.kt`: Gestión del estado (`UiState`) y flujos reactivos (`flatMapLatest`).
* `ui/screens/AmiiboListScreen.kt`: Interfaz de usuario declarativa con manejo de estados exhaustivo.

---

## 🎥 Video de explicación:

[(https://youtu.be/wxPR03D4R28)]
