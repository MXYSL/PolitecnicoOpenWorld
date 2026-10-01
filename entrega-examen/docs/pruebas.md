# Plan y resultados de QA

## Información general

**Proyecto:** PolitecnicoOpenWorld  
**Rama de implementación:** `fix/game-feedback-and-exit-flow`  
**SHA base:** `7ed325393f82872c2be94ff2ada46948efa19152`  
**SHA probado:** `f808274d6cf4c2d872a92f474db79abaab68811a`  
**Fecha:** 1 de octubre de 2026  

## Entorno

- Sistema operativo: Windows 11
- Android Studio: Quail 4 | 2026.1.4
- Build Android Studio: AI-261.26222.65.2614.16204760
- Android Studio Runtime: OpenJDK 25.0.3
- Gradle: 9.5.0
- JDK local de Gradle: Amazon Corretto 25.0.4.1
- AVD: Pixel 8
- Android: 17
- API: 37
- Arquitectura: x86_64

## Cambios evaluados

1. Cambio de `BACK / VOLVER` por `EXIT TO MENU / SALIR AL MENÚ`.
2. Retroalimentación sonora al seleccionar un personaje.

## Criterios de aceptación

- AC-01: Settings muestra `EXIT TO MENU` en inglés.
- AC-02: Settings muestra `SALIR AL MENÚ` en español.
- AC-03: El botón inferior continúa navegando al menú principal.
- AC-04: La flecha superior continúa regresando a la pantalla anterior.
- AC-05: Con SFX habilitado se reproduce una confirmación al seleccionar personaje.
- AC-06: Con SFX en cero la selección continúa normalmente.

## Riesgos

### R-01 - Regresión de navegación
Impacto: medio.  
El cambio de etiqueta podría afectar accidentalmente el comportamiento del botón.  
Cubierto por TC-01, TC-03 y TC-04.

### R-02 - Dependencia del flujo respecto al audio
Impacto: alto.  
Una falla en la reproducción de audio no debe impedir la selección del personaje.  
Cubierto por TC-05 y TC-06.

### R-03 - Problemas de presentación
Impacto: bajo.  
El texto más largo podría recortarse con fuente ampliada u otra orientación.  
Cubierto por TC-07 y TC-08.

---

## TC-01 - Exit to Menu en inglés

Categoría: Ruta feliz  
Criterios: AC-01, AC-03  
SHA: `f808274d6cf4c2d872a92f474db79abaab68811a`

Pasos:
1. Abrir la aplicación en inglés.
2. Entrar a Settings.
3. Verificar el botón inferior.
4. Pulsar `EXIT TO MENU`.

Esperado:
El texto muestra `EXIT TO MENU` y navega al menú principal.

Resultado real:
El botón mostró `EXIT TO MENU` y la navegación al menú principal se realizó correctamente.

Estado: APROBADO.

Evidencia: [TC01_exit_to_menu_en.png](../evidencias/TC01_exit_to_menu_en.png)

---

## TC-02 - Salir al menú en español

Categoría: Condición alternativa  
Criterio: AC-02  
SHA: `f808274d6cf4c2d872a92f474db79abaab68811a`

Pasos:
1. Configurar Android en español.
2. Abrir la aplicación.
3. Entrar a Ajustes.
4. Verificar el botón inferior.

Esperado:
El botón muestra `SALIR AL MENÚ`.

Resultado real:
La traducción `SALIR AL MENÚ` se mostró correctamente.

Estado: APROBADO.

Evidencia: [TC02_salir_al_menu_es.png](../evidencias/TC02_salir_al_menu_es.png)

---

## TC-03 - Flecha superior desde Free Roam

Categoría: Regresión  
Criterio: AC-04  
Riesgo: R-01  
SHA: `f808274d6cf4c2d872a92f474db79abaab68811a`

Pasos:
1. Entrar a Free Roam.
2. Abrir Settings.
3. Pulsar la flecha superior de regreso.

Esperado:
Regresa a Free Roam y no al menú principal.

Resultado real:
La flecha superior regresó correctamente a Free Roam.

Estado: APROBADO.

Evidencia: [TC03_back_to_free_roam.mp4](../evidencias/TC03_back_to_free_roam.mp4)

---

## TC-04 - Exit to Menu desde Free Roam

Categoría: Navegación y estado  
Criterio: AC-03  
Riesgo: R-01  
SHA: `f808274d6cf4c2d872a92f474db79abaab68811a`

Pasos:
1. Entrar a Free Roam.
2. Abrir Settings.
3. Pulsar `EXIT TO MENU`.

Esperado:
La aplicación sale de Free Roam y muestra el menú principal.

Resultado real:
La navegación al menú principal se realizó correctamente.

Estado: APROBADO.

Evidencia: [TC04_exit_free_roam.mp4](../evidencias/TC04_exit_free_roam.mp4)

---

## TC-05 - Sonido al seleccionar personaje

Categoría: Ruta feliz  
Criterio: AC-05  
Riesgo: R-02  
SHA: `f808274d6cf4c2d872a92f474db79abaab68811a`

Pasos:
1. Configurar SFX con volumen audible.
2. Entrar a Story Mode.
3. Iniciar New Game.
4. Seleccionar Estudiante.

Esperado:
Se reproduce una confirmación sonora y continúa al selector de slot.

Resultado real:
Se reprodujo el efecto y el flujo continuó correctamente al selector de slot.

Estado: APROBADO.

Evidencia: [TC05_character_sound.mp4](../evidencias/TC05_character_sound.mp4)

---

## TC-06 - Selección con SFX en cero

Categoría: Condición límite  
Criterio: AC-06  
Riesgo: R-02  
SHA: `f808274d6cf4c2d872a92f474db79abaab68811a`

Pasos:
1. Configurar SFX en cero.
2. Entrar a Story Mode.
3. Iniciar New Game.
4. Seleccionar un personaje.

Esperado:
No hay sonido audible, pero la selección continúa al selector de slot.

Resultado real:
No se escuchó el efecto y el flujo de selección continuó normalmente.

Estado: APROBADO.

Evidencia: [TC06_sfx_zero.mp4](../evidencias/TC06_sfx_zero.mp4)

---

## TC-07 - Fuente ampliada

Categoría: Accesibilidad  
Riesgo: R-03  
SHA: `f808274d6cf4c2d872a92f474db79abaab68811a`

Pasos:
1. Aumentar el tamaño de fuente de Android.
2. Abrir Settings.
3. Revisar el botón de salida.

Esperado:
El texto continúa visible, legible y el botón sigue siendo utilizable.

Resultado real:
El botón permaneció legible y utilizable con la fuente ampliada.

Estado: APROBADO.

Evidencia: [TC07_large_font.png](../evidencias/TC07_large_font.png)

---

## TC-08 - Orientaciones de pantalla

Categoría: Compatibilidad / entorno  
Riesgo: R-03  
SHA: `f808274d6cf4c2d872a92f474db79abaab68811a`

Pasos:
1. Abrir Settings desde el menú principal en vertical.
2. Verificar el botón.
3. Entrar a Free Roam.
4. Abrir Settings en horizontal.
5. Verificar nuevamente el botón.

Esperado:
El botón permanece visible y funcional en ambas configuraciones.

Resultado real:
El control se mostró correctamente tanto en vertical como en horizontal.

Estado: APROBADO.

Evidencias:

- [TC08_portrait.png](../evidencias/TC08_portrait.png)
- [TC08_landscape.png](../evidencias/TC08_landscape.png)

---

## Verificación automática local

Comando:

`.\gradlew.bat :app:assembleDebug :app:testDebugUnitTest :shared:testAndroidHostTest --stacktrace`

Resultado:

`BUILD SUCCESSFUL in 21s`

`79 actionable tasks: 10 executed, 69 up-to-date`

Estado: APROBADO.

## Decisión de calidad

Los ocho casos manuales fueron ejecutados sobre el SHA
`f808274d6cf4c2d872a92f474db79abaab68811a`.

Los criterios de aceptación definidos para los dos cambios fueron satisfechos y no se detectaron regresiones bloqueantes durante las pruebas realizadas.

Con la evidencia disponible, se recomienda integrar el cambio.

Riesgos restantes:
las pruebas se realizaron sobre un Pixel 8 virtual con Android 17 / API 37, por lo que otros dispositivos físicos y configuraciones no fueron evaluados exhaustivamente.