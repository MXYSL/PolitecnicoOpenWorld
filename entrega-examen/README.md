\# Primer examen parcial - Pull Request con QA



\## Datos generales



\*\*Alumno:\*\* Mayra Solis Lugo

\*\*Equipo:\*\*   

\*\*GitHub:\*\* MXYSL  

\*\*Proyecto:\*\* PolitecnicoOpenWorld  



\## Objetivo



Preparar, probar y someter a revisión una contribución pequeña al proyecto PolitecnicoOpenWorld mediante un Pull Request con aseguramiento de calidad reproducible.



\## Alcance



La contribución contiene dos mejoras:



1\. Clarificación del botón de salida de Settings mediante `EXIT TO MENU / SALIR AL MENÚ`.

2\. Retroalimentación sonora al seleccionar un personaje.



\## Issue



https://github.com/MXYSL/PolitecnicoOpenWorld/issues/2



\## Pull Request



\[URL DEL PR]



\## Versiones



\*\*SHA base:\*\*  

`7ed325393f82872c2be94ff2ada46948efa19152`



\*\*SHA de implementación probado:\*\*  

`f808274d6cf4c2d872a92f474db79abaab68811a`



\## Commits de implementación



\- `a825da84` - `fix: clarify settings exit action`

\- `f808274d` - `feat: add sound feedback to character selection`



\## QA



\[Matriz y resultados de pruebas](docs/pruebas.md)



Las pruebas incluyen:



\- ruta feliz;

\- condición alterna/límite;

\- regresión;

\- navegación y estado;

\- accesibilidad;

\- compatibilidad/entorno.



\## Evidencias



Las evidencias se encuentran en:



\[evidencias/](evidencias/)



\## Verificación local



Se ejecutó:



`.\\gradlew.bat :app:assembleDebug :app:testDebugUnitTest :shared:testAndroidHostTest --stacktrace`



Resultado:



`BUILD SUCCESSFUL in 21s`



\## CI / Checks



Revisar los Checks del Pull Request:



\[URL DEL PR]/checks



\## Revisión técnica



Pendiente de registrar el enlace al comentario/review realizado por un compañero.



\## Conclusión



Los cambios fueron evaluados mediante ocho casos manuales y las verificaciones automáticas locales del proyecto.



Los criterios de aceptación fueron satisfechos en el entorno documentado y no se detectaron regresiones bloqueantes durante la ejecución realizada.





La implementación, ejecución de pruebas y evidencias fueron realizadas y verificadas por el alumno.

