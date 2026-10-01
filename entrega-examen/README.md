# First Partial Exam - Pull Request with QA

## General Information

**Student:** Mayra Solis Lugo  
**GitHub:** MXYSL  
**Project:** PolitecnicoOpenWorld  
**Implementation branch:** `fix/game-feedback-and-exit-flow`  
**Academic delivery branch:** `exam1-delivery`

---

## Objective

Prepare, test, document, and submit a small Android contribution to the
PolitecnicoOpenWorld project through a Pull Request with reproducible
quality-assurance evidence.

---

## Contribution Scope

This contribution contains two focused interaction improvements:

1. Clarify the Settings exit action by replacing the generic
   `BACK / VOLVER` label with `EXIT TO MENU / SALIR AL MENÚ`.

2. Add sound feedback when selecting a character before starting
   a new Story Mode game.

### Out of Scope

- Story Mode save logic
- Character movement
- New audio assets
- Navigation redesign
- Multiplayer changes

---

# Issue

[MXYSL/PolitecnicoOpenWorld #2](https://github.com/MXYSL/PolitecnicoOpenWorld/issues/2)

---

# Pull Request

[gabrielhuav/PolitecnicoOpenWorld #177](https://github.com/gabrielhuav/PolitecnicoOpenWorld/pull/177)

---

# Changes

## Change 1 - Settings Exit Action

### Before

The bottom Settings button displayed:

`BACK`

or:

`VOLVER`

However, this button does not simply return to the previous screen.

Its actual behavior is to exit the current screen and navigate to the
Main Menu.

### After - English

The label was changed to:

`EXIT TO MENU`

### Evidence - TC-01

<img
  src="evidencias/TC01_exit_to_menu_en.png"
  width="500"
  alt="EXIT TO MENU button in English"
/>

**Observed result:**  
The Settings screen correctly displayed `EXIT TO MENU`, matching the
actual navigation behavior of the button.

**Status:** PASSED

---

### After - Spanish

The Spanish label was changed to:

`SALIR AL MENÚ`

### Evidence - TC-02

<img
  src="evidencias/TC02_salir_al_menu_es.png"
  width="500"
  alt="SALIR AL MENÚ button in Spanish"
/>

**Observed result:**  
The Spanish localization correctly displayed `SALIR AL MENÚ`.

**Status:** PASSED

---

## Change 1 - Before / After Summary

| Before | After - English | After - Spanish |
| --- | --- | --- |
| `BACK / VOLVER` did not clearly describe that the action exits to the Main Menu. | <img src="evidencias/TC01_exit_to_menu_en.png" width="300" alt="EXIT TO MENU English"> | <img src="evidencias/TC02_salir_al_menu_es.png" width="300" alt="SALIR AL MENÚ Spanish"> |

The existing navigation behavior was preserved.

Only the user-facing label was changed so that the control describes
what it actually does.

---

# Change 2 - Character Selection Feedback

## Before

Character selection continued directly to the save-slot selection screen:

```kotlin
onClick = {
    onPick(opt.skin)
}
