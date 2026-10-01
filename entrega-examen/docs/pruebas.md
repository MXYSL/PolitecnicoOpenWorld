# QA Plan and Results

## General information

**Project:** PolitecnicoOpenWorld  
**Implementation branch:** `fix/game-feedback-and-exit-flow`  
**Base SHA:** `7ed325393f82872c2be94ff2ada46948efa19152`  
**Tested SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`  
**Date:** October 1, 2026

## Environment

- Operating system: Windows 11
- Android Studio: Quail 4 | 2026.1.4
- Android Studio build: AI-261.26222.65.2614.16204760
- Android Studio Runtime: OpenJDK 25.0.3
- Gradle: 9.5.0
- Local Gradle JDK: Amazon Corretto 25.0.4.1
- AVD: Pixel 8
- Android: 17
- API: 37
- Architecture: x86_64

## Evaluated changes

1. Replace `BACK / VOLVER` with `EXIT TO MENU / SALIR AL MENÚ`.
2. Add sound feedback when selecting a character.

## Acceptance criteria

- AC-01: Settings displays `EXIT TO MENU` in English.
- AC-02: Settings displays `SALIR AL MENÚ` in Spanish.
- AC-03: The bottom button still navigates to the Main Menu.
- AC-04: The top back arrow still returns to the previous screen.
- AC-05: With SFX enabled, selecting a character plays one confirmation sound.
- AC-06: With SFX set to zero, character selection still completes normally.

## Risks

### R-01 - Navigation regression
**Impact:** Medium.  
The label change could accidentally alter the existing exit behavior.  
**Covered by:** TC-01, TC-03 and TC-04.

### R-02 - Audio dependency in character selection
**Impact:** High.  
A sound playback problem must not prevent character selection from continuing.  
**Covered by:** TC-05 and TC-06.

### R-03 - Localization mismatch
**Impact:** Low.  
The new exit label could be correct in one language but incorrect or missing in another.  
**Covered by:** TC-01 and TC-02.

---

## TC-01 - Exit to Menu in English

**Category:** Happy path  
**Criteria:** AC-01, AC-03  
**Risk:** R-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Steps
1. Open the application in English.
2. Open Settings.
3. Verify the bottom button.
4. Tap `EXIT TO MENU`.

### Expected result
The button displays `EXIT TO MENU` and navigates to the Main Menu.

### Actual result
The button displayed `EXIT TO MENU` and navigation to the Main Menu worked correctly.

**Status:** PASSED.

**Evidence:** [TC01_exit_to_menu_en.png](../evidencias/TC01_exit_to_menu_en.png)

---

## TC-02 - Exit label in Spanish

**Category:** Compatibility / environment (language)  
**Criterion:** AC-02  
**Risk:** R-03  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Steps
1. Configure Android in Spanish.
2. Open the application.
3. Open Settings.
4. Verify the bottom button.

### Expected result
The button displays `SALIR AL MENÚ`.

### Actual result
The `SALIR AL MENÚ` translation was displayed correctly.

**Status:** PASSED.

**Evidence:** [TC02_salir_al_menu_es.png](../evidencias/TC02_salir_al_menu_es.png)

---

## TC-03 - Top back arrow from Free Roam

**Category:** Regression  
**Criterion:** AC-04  
**Risk:** R-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Steps
1. Enter Free Roam.
2. Open Settings.
3. Tap the top back arrow.

### Expected result
The application returns to Free Roam instead of the Main Menu.

### Actual result
The top back arrow returned correctly to Free Roam.

**Status:** PASSED.

**Evidence:** [TC03_back_to_free_roam.webm](../evidencias/TC03_back_to_free_roam.webm)

---

## TC-04 - Exit to Menu from Free Roam

**Category:** Navigation and state  
**Criterion:** AC-03  
**Risk:** R-01  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Steps
1. Enter Free Roam.
2. Open Settings.
3. Tap `EXIT TO MENU`.

### Expected result
The application exits Free Roam and displays the Main Menu.

### Actual result
Navigation to the Main Menu completed correctly.

**Status:** PASSED.

**Evidence:** [TC04_exit_free_roam.mp4](../evidencias/TC04_exit_free_roam.mp4)

---

## TC-05 - Character-selection sound

**Category:** Happy path  
**Criterion:** AC-05  
**Risk:** R-02  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Steps
1. Set SFX volume to an audible level.
2. Enter Story Mode.
3. Start New Game.
4. Select Estudiante.

### Expected result
One confirmation sound plays and the flow continues to the save-slot selector.

### Actual result
The effect played and the flow continued correctly to the save-slot selector.

**Status:** PASSED.

**Evidence:** [TC05_character_sound.mp4](../evidencias/TC05_character_sound.mp4)

---

## TC-06 - Character selection with SFX set to zero

**Category:** Limit condition  
**Criterion:** AC-06  
**Risk:** R-02  
**SHA:** `f808274d6cf4c2d872a92f474db79abaab68811a`

### Steps
1. Set SFX volume to zero.
2. Enter Story Mode.
3. Start New Game.
4. Select a character.

### Expected result
No sound is audible, but character selection still continues to the save-slot selector.

### Actual result
No effect was audible and character selection continued normally.

**Status:** PASSED.

**Evidence:** [TC06_sfx_zero.mp4](../evidencias/TC06_sfx_zero.mp4)

---

## Local automated verification

Command:

```powershell
.\gradlew.bat :app:assembleDebug :app:testDebugUnitTest :shared:testAndroidHostTest --stacktrace
```

Result:

```text
BUILD SUCCESSFUL in 21s
79 actionable tasks: 10 executed, 69 up-to-date
```

**Status:** PASSED.

## QA decision

Six manual cases were executed against SHA
`f808274d6cf4c2d872a92f474db79abaab68811a`.

The defined acceptance criteria for the two implemented changes were satisfied in the documented environment, and no blocking regression was observed in the executed cases.

### Remaining limitation

A dedicated large-font / TalkBack accessibility scenario was not included in the retained evidence set, so accessibility under those conditions is not claimed as verified.

Testing was performed on a Pixel 8 virtual device with Android 17 / API 37; physical devices and additional Android versions were not exhaustively evaluated.
