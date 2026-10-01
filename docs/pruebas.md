# Matriz de pruebas - Game feedback and exit flow

## Información general

**Proyecto:** PolitecnicoOpenWorld  
**Rama:** `fix/game-feedback-and-exit-flow`

**SHA base:**  
`7ed325393f82872c2be94ff2ada46948efa19152`

**SHA final probado:**  
`f808274d6cf4c2d872a92f474db79abaab68811a`

## Cambios incluidos

### Cambio 1 - Claridad de la acción de salida de Settings

Antes, el botón inferior de la pantalla Settings mostraba:

- `BACK` en inglés.
- `VOLVER` en español.

Sin embargo, su acción real era salir de Settings y navegar al menú principal.

Después del cambio, el texto se modificó a:

- `EXIT TO MENU` en inglés.
- `SALIR AL MENÚ` en español.

La navegación existente no fue modificada.

### Cambio 2 - Retroalimentación sonora al seleccionar personaje

Antes, seleccionar un personaje en una partida nueva continuaba al selector de
slot sin proporcionar una confirmación sonora específica.

Después del cambio, al seleccionar un personaje se reproduce un efecto de
sonido existente mediante `SoundManager.playItem()` antes de continuar con el
flujo normal.

No se agregaron nuevos archivos de audio.

---

# Criterios de aceptación

## AC-01

El botón inferior de Settings debe mostrar `EXIT TO MENU` cuando la aplicación
está en inglés.

## AC-02

El botón inferior de Settings debe mostrar `SALIR AL MENÚ` cuando la aplicación
está en español.

## AC-03

El cambio de texto no debe modificar el comportamiento existente de navegación:
el botón inferior debe seguir llevando al menú principal.

## AC-04

La flecha superior de Settings debe conservar su comportamiento de regreso a la
pantalla anterior.

## AC-05

Al seleccionar un personaje para una partida nueva con SFX audible, debe
reproducirse una sola confirmación sonora y el flujo debe continuar al selector
de slot.

## AC-06

Con el volumen SFX en cero, la selección del personaje debe seguir funcionando,
aunque el sonido no sea audible.

---

# Riesgos identificados

## R-01 - Regresión de navegación

El cambio del botón inferior podría alterar accidentalmente la acción que
actualmente lleva al menú principal.

**Impacto:** Medio  
**Casos relacionados:** TC-01, TC-03, TC-04

## R-02 - Sonido duplicado

La selección del personaje podría reproducir más de una vez el efecto de
confirmación.

**Impacto:** Bajo  
**Casos relacionados:** TC-05

## R-03 - Dependencia entre audio y selección

Un problema al reproducir el sonido podría impedir que `onPick()` continúe con
el flujo normal de selección de personaje.

**Impacto:** Alto  
**Casos relacionados:** TC-05, TC-06

---

# Entorno de pruebas

**Sistema operativo:** Windows 11  
**Gradle:** 9.5.0  
**SHA probado:** `f808274d6cf4c2d872a92f474db79abaab68811a`

**Dispositivo / AVD:** PENDIENTE DE REGISTRAR  
**API Android:** PENDIENTE DE REGISTRAR  
**Orientación utilizada:** vertical y horizontal según el caso

---

# Casos de prueba

## TC-01 - Exit to Menu en inglés

**Categoría:** Happy path  
**Criterios:** AC-01, AC-03  
**Riesgo:** R-01  
**Autor:** [TU NOMBRE]  
**Fecha:** 2026-10-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Precondiciones

1. La aplicación está configurada en inglés.
2. La aplicación está instalada desde el build de la rama evaluada.

### Pasos

1. Abrir la aplicación.
2. Entrar a Settings.
3. Localizar el botón inferior.
4. Verificar el texto mostrado.
5. Pulsar el botón.

### Resultado esperado

El botón muestra `EXIT TO MENU` y, al pulsarlo, la aplicación navega al menú
principal.

### Resultado real

PENDIENTE DE EJECUTAR.

### Estado

PENDIENTE.

### Evidencia

PENDIENTE.

---

## TC-02 - Salir al menú en español

**Categoría:** Alternativa  
**Criterio:** AC-02  
**Riesgo:** R-01  
**Autor:** [TU NOMBRE]  
**Fecha:** 2026-10-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Precondiciones

1. La aplicación está configurada en español.
2. La aplicación está instalada desde el build de la rama evaluada.

### Pasos

1. Abrir la aplicación.
2. Entrar a Settings.
3. Localizar el botón inferior.
4. Verificar el texto mostrado.
5. Pulsar el botón.

### Resultado esperado

El botón muestra `SALIR AL MENÚ` y lleva al menú principal.

### Resultado real

PENDIENTE DE EJECUTAR.

### Estado

PENDIENTE.

### Evidencia

PENDIENTE.

---

## TC-03 - Regresión de la flecha superior

**Categoría:** Regresión  
**Criterio:** AC-04  
**Riesgo:** R-01  
**Autor:** [TU NOMBRE]  
**Fecha:** 2026-10-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Precondiciones

1. Estar dentro de Free Roam.
2. Abrir Settings desde el juego.

### Pasos

1. Entrar a Free Roam.
2. Pulsar el botón de Settings.
3. Pulsar la flecha superior de regreso.

### Resultado esperado

La aplicación regresa a Free Roam y no al menú principal.

### Resultado real

PENDIENTE DE EJECUTAR.

### Estado

PENDIENTE.

### Evidencia

PENDIENTE.

---

## TC-04 - Exit to Menu desde Free Roam

**Categoría:** Navegación / estado  
**Criterios:** AC-01, AC-03  
**Riesgo:** R-01  
**Autor:** [TU NOMBRE]  
**Fecha:** 2026-10-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Precondiciones

1. Estar dentro de Free Roam.
2. Abrir Settings desde el juego.

### Pasos

1. Entrar a Free Roam.
2. Abrir Settings.
3. Pulsar `EXIT TO MENU`.

### Resultado esperado

La aplicación abandona Free Roam y navega al menú principal.

### Resultado real

PENDIENTE DE EJECUTAR.

### Estado

PENDIENTE.

### Evidencia

PENDIENTE.

---

## TC-05 - Sonido al seleccionar personaje

**Categoría:** Happy path / retroalimentación  
**Criterio:** AC-05  
**Riesgos:** R-02, R-03  
**Autor:** [TU NOMBRE]  
**Fecha:** 2026-10-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Precondiciones

1. El volumen de efectos SFX es mayor a cero.
2. Se inicia el flujo de una nueva partida de Story Mode.

### Pasos

1. Entrar a Story Mode.
2. Seleccionar una escuela disponible.
3. Seleccionar New Game.
4. Esperar a que aparezca la selección de personaje.
5. Pulsar `Estudiante`.

### Resultado esperado

1. Se reproduce una sola confirmación sonora.
2. El personaje se selecciona correctamente.
3. La aplicación continúa al selector de slot para guardar o sobrescribir.

### Resultado real

Se reprodujo el efecto de selección y la aplicación continuó correctamente al
selector de slot.

### Estado

APROBADO.

### Evidencia

Agregar enlace o video de la ejecución.

---

## TC-06 - Selección de personaje con SFX en cero

**Categoría:** Límite  
**Criterio:** AC-06  
**Riesgo:** R-03  
**Autor:** [TU NOMBRE]  
**Fecha:** 2026-10-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Precondiciones

1. Configurar el volumen SFX en `0`.
2. Iniciar una nueva partida de Story Mode.

### Pasos

1. Abrir Settings.
2. Establecer SFX en 0.
3. Regresar al menú principal.
4. Entrar a Story Mode.
5. Iniciar New Game.
6. Seleccionar un personaje.

### Resultado esperado

No se escucha el efecto, pero el personaje se selecciona y la aplicación
continúa normalmente al selector de slot.

### Resultado real

PENDIENTE DE EJECUTAR.

### Estado

PENDIENTE.

### Evidencia

PENDIENTE.

---

## TC-07 - Accesibilidad con texto aumentado

**Categoría:** Accesibilidad  
**Criterio:** AC-01 / AC-02  
**Autor:** [TU NOMBRE]  
**Fecha:** 2026-10-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Precondiciones

1. Aumentar el tamaño de fuente de Android.
2. Abrir la aplicación con la configuración aplicada.

### Pasos

1. Entrar a Settings.
2. Localizar `EXIT TO MENU` o `SALIR AL MENÚ`.
3. Verificar que el botón sea legible.
4. Pulsar el botón.

### Resultado esperado

El texto continúa siendo legible y el control continúa siendo utilizable.

### Resultado real

PENDIENTE DE EJECUTAR.

### Estado

PENDIENTE.

### Evidencia

PENDIENTE.

---

## TC-08 - Compatibilidad de orientación

**Categoría:** Compatibilidad / entorno  
**Criterios:** AC-01, AC-03  
**Autor:** [TU NOMBRE]  
**Fecha:** 2026-10-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Precondiciones

Aplicación instalada desde el SHA evaluado.

### Pasos

1. Abrir Settings desde el menú principal.
2. Verificar la pantalla en orientación vertical.
3. Regresar.
4. Entrar a Free Roam.
5. Abrir Settings desde el juego.
6. Verificar la pantalla en orientación horizontal.

### Resultado esperado

En ambas configuraciones el botón de salida permanece visible, legible y
funcional.

### Resultado real

PENDIENTE DE EJECUTAR.

### Estado

PENDIENTE.

### Evidencia

PENDIENTE.

---

# Validación automatizada local

Desde el directorio interno del proyecto se ejecutó:

```powershell
.\gradlew.bat :app:assembleDebug :app:testDebugUnitTest :shared:testAndroidHostTest --stacktrace
