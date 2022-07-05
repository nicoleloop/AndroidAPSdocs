Notas de la versión
**************************************************
Siga las instrucciones en el manual ` manual de actualización <../Installing-AndroidAPS/Update-to-new-version.html>`_. También puede encontrar una sección de resolución de problemas que se ocupa de las dificultades más comunes cuando se actualiza en la página de actualización manual.

Recibirá la siguiente información tan pronto como se disponga de una nueva actualización:

.. imagen:: ../images/AAPS_LoopDisable90days.png
  :alt: Información de la actualización

Entonces tienes 60 días para actualizar. Si no actualiza dentro de estos 60 días, la AAPS retrocederá a LGS (suspensión de glucosa baja -ver `glosario <../Getting-Started/Glossary.html>`_) como en el `objetivo 6 <../Usage/Objectives.html>`_.

Si no se actualiza durante otros 30 días (90 días a partir de la fecha de la nueva versión), AAPS cambiará a Lazo Abierto.

Por favor, entienda que este cambio no tiene la intención de molestarlo, sino que se debe a razones de seguridad. Las nuevas versiones de AndroidAPS no sólo proporcionan nuevas características, sino también importantes arreglos de seguridad. Por lo tanto, es necesario actualizar lo antes posible. Desafortunadamente, todavía hay informes de error de versiones muy antiguas, por lo que esto es un intento de mejorar la seguridad para cada usuario y toda la comunidad de DIY. Gracias por tu comprensión.

Versión de Android y versión de AAPS
====================================
Si tu teléfono móvil utiliza una versión de Android inferior a Android 9, no podrás usar la versión AAPS 3.0.0, ya que la nueva versión requiere al menos la versión de Android 9.

Se han lanzado nuevas versiones de AAPS que sólo comprueban la versión de Android del teléfono, para permitir a los usuarios instalar versiones anteriores de AAPS en teléfonos con versiones de Android inferiores a Android 9. No se incluyen otras mejoras.

Android 9 y superiores
------------------------------------
* Usar la última versión de AAPS
* Descargar el código fuente de AAPS desde https://github.com/nightscout/AndroidAPS

Android 8
------------------------------------
* Usar la versión de AAPS **2.8.2.1**
* Descargar el código de AAPS desde https://github.com/nightscout/AndroidAPS branch 2.8.2.1

Android 7
------------------------------------
* Usar la versión de AAPS **2.6.2**
* Descargar el código de AAPS desde https://github.com/nightscout/AndroidAPS branch 2.6.2

Versión 3.1.0
================
Fecha de lanzamiento: XX-XX-2022

Notas importantes
----------------------
* Después de actualizar, desinstalar la aplicación Wear del reloj e instalar la nueva versión (no se puede actualizar directamente)
* Usuarios de Omnipod: Actualizar cuando toque cambio del POD

Cambios
----------------------
* Corrección de errores de la versión 3.0
* Corrección de congelación de la aplicación @MilosKozak
* Correcciones de los controladores de las bombas DASH @avereha
* Corrección de controladores de las bombas Dana @MilosKozak
* Importantes mejoras de la interfaz gráfica (UI), limpieza y unificación. Migración a "Material Design", estilos, tema claro, nuevos iconos, etc. @Andries-Smit @MilosKozak @osodebailar @Philoul
* Añadido Widget @MilosKozak
* Aidex CGM support @andyrozman @markvader (Pumpcontrol only)
* Tarjetas Wear y traducciones @Andries-Smith
* Código Wear refactorizado No compatible con versiones anteriores @MilosKozak
* Mejoras A11Y (Mejoras de accesibilidad) @Andries-Smith
* Nueva opción de protección PIN @Andries-Smit
* Permite cambiar la escala gráfica desde el menú @MilosKozak
* Más estadísticas disponibles @MilosKozak
* Complemento MDI eliminado en favor de la Bomba Virtual

Versión 3.0.0
================
Fecha de lanzamiento: 31-01-2022

Notas importantes
----------------------
* **La versión mínima de Android requerida es la 9.0.**
* **Los datos no se migran a la nueva base de datos.** Los cambios son tan importantes que simplemente no es posible hacerlo. Debido a esto, después de actualizar a la nueva versión, la insulina activa (IOB), carbohidratos (COB), tratamientos, etc. serán eliminados. Tienes que crear un nuevo `cambio de perfil <../Usage/Profiles.html>`_ y empezar con los valores de insulina activa (IOB) y carbohidratos (COB) a cero. ¡Planifica la actualización con cuidado! La mejor situación para realizar la actualización es cuando no tengamos insulina activa ni carbohidratos.
* Usa la misma versión de AAPS y NSClient

**Asegúrate de comprobar y ajustar las configuraciones después de actualizar a la versión 3.0, tal y como se describe** `aquí<../Installing-AndroidAPS/update3_0.html>`__.

Pasos de preparación
----------------------
**Al menos dos días antes de la actualización:**

* Deshabilitar el "puente" entre Dexcom y Nightscout
* Si estás usando Dexcom G5/G6 y xDrip+ como recolector, tienes que actualizar al menos a la versión de xDrip+ del 14 de Enero de 2022 
* Si estás usando G5/G6, es recomendable cambiar a BYODA, ya que permite el suavizado de datos (puedes seguir usando xDrip+ para otros propósitos, xDrip puede recibir los datos de BYODA)


Cambios
----------------------
* 100k lineas cambiadas, 105k nuevas líneas de código
* `Soporte Omnipod DASH <../Configuration/OmnipodDASH.html>`_ @AdrianLxM @avereha @bartsopers @vanelsberg
* `Soporte para Dana-i <../Configuration/DanaRS-Insulin-Pump.html>`_ @MilosKozak
* `Soporte DiaconnG8 <../Configuration/DiaconnG8.html>`_
* Soporte para Glunovo
* Base de datos interna actualizada a Room @MilosKozak @Tebbe @AdrianLxm @Philoul @andyrozman
* Gran cantidad de código reescrito a Kotlin @MilosKozak
* Nueva interfaz interna para controladores de bombas
* NSClient reescrito para mejorar la sincronización y una personalización más detallada @MilosKozak

  * No se permite eliminar registros de NS (Sólo se pueden invalidar mediante NSClient)
  * No se permite la modificación de registros de NS
  * Disponible la sincronización de la configuración sin necesidad de habilitar el modo de ingeniería (para padres)
  * Posibilidad de resincronizar datos

* Cambio en el comportamiento del cambio de perfil. Ahora se hace una distinción entre Cambio de Perfil *(realizado por el usuario)* y el Cambio de Perfil *(cuando el cambio es ejecutado por la bomba)* @MilosKozak @Tebbe
* Puedes comenzar el objetivo temporal de actividad desde el cambio de perfil @MilosKozak
* NSProfile ha desaparecido, sólo se puede utilizar el perfil local. El perfil local puede ser `Sincronizado a Nightscout <../Installing-AndroidAPS/update3_0.html#nightscout-profile-cannot-be-pushed>`_. @MilosKozak.
* Procedimiento de `restablecimiento de la contraseña maestra <../Installing-AndroidAPS/update3_0.html#reset-master-password>`_ @MilosKozak
* Seguimiento de las acciones del usuario @Philoul
* Nuevo desencadenador llamado TempTargetValue disponible en las automatizaciones @Philoul
* Nueva acción de automatización Careportal @Philoul
* Añadido recordatorio de bolo en el diálogo de carbohidratos @Philoul
* Asistente de bolos mejorado
* Mejoras en la interfaz del usuario @MilosKozak
* Nuevos botones de usuario para las automatizaciones @MilosKozak
* Nuevo diseño de las automatizaciones @MilosKozak
* El navegador del historial ha sido actualizado y corregido @MilosKozak
* Objetivo 9 eliminado @MilosKozak
* Corregido un problema asociado a datos inestables del MCG @MilosKozak
* Mejoras de comunicación para DanaR y DanaRS @MilosKozak
* Integración con CircleCI @MilosKozak
* Cambios en la ubicación de ficheros:

   * /AAPS/extra (modo ingeniearía)
   * /AAPS/logs /AAPS/exports
   * /AAPS/preferences

Versión 2.8.2
================
Fecha de lanzamiento: 23-01-2021

* Por favor, revise también `important hints for version 2.8.1.1 <../Installing-AndroidAPS/Releasenotes.html#important-hints>`_ más abajo.

Cambios
----------------------
* Mejoras de estabilidad
* Más ajustes para Android 8+
* Mejoras en los iconos
* Mejores en relojes
* Correcciones en NSClient
* La calculadora de bolos ahora trabaja con Pumpcontrol y NSClient

Versión 2.8.1.1
================
Fecha de lanzamiento: 12-01-2021

Notas importantes
----------------------
* Opción **NS_UPLOAD_ONLY** ha sido forzada a ON para todos los usuarios de la versión 2.8.1.
* Si estás usando NSClient para establecer objetevos temporales (OT) carbohidratos (COB) o para realizar cambios de perfil, debes desactivar esta opción en AAPS, pero **sólo en caso de que la sincronización funcione bien (p. ej.  no ves cambios no deseados, como la mofificación automática de OT, TBR, etc.)
* ATENCIÓN: No hagas esto si usas otras aplicaciones para gestionar tratamientos (como xDrip+ con emisión de datos locales/subidas/sincronización,...).
* NS_UPLOAD_ONLY sólo puede desactivarse si tenemos activo el modo de ingeniería.

Cambios principales
----------------------
* Mejoras y correcciones con RileyLink y bombas Omnipod y MDT 
* La opción NS_UPLOAD_ONLY es forzada
* Correcciones en SMB y en la aplicación de Dexcom
* Correcciones en las esferas de relojes
* Mejoras en los informes de errores
* Se ha revertido Gradle para permitir la instalación de esferas de forma directa en los relojes
* Correcciones en las automatizaciones
* Mejoras en los controladores RS
* Se han corregido varios problemas que provocaban que AAPS fallara
* Correcciones y mejoras en la interfaz gráfica
* Nuevos idiomas soportados

Versión 2.8.0
================
Fecha de lanzamiento: 01-01-2021

Notas importantes
----------------------
* **Minimum Android version is 8.0 now.** For older Android versions you can still use 2.6.1.4 from old repo.
* `Objectives have changed. <../Usage/Objectives.html#objective-3-prove-your-knowledge>`_ **Finish not completed objectives before update.**
* Repository location still on https://github.com/nightscout/AndroidAPS . If you are not familiar with git the easiest way for update is remove directory with AndroidAPS and do a `new clone <../Installing-AndroidAPS/Building-APK.html>`_.
* Please use `Android Studio 4.1.1 <https://developer.android.com/studio/>`_ or newer to build the apk.

Nuevas características importantes
----------------------
* `Omnipod Eros support <../Configuration/OmnipodEros.html>`_ @bartsopers @andyrozman @ktomy @samspycher @TeleRiddler @vanelsberg @eurenda and special thanks to @ps2 @itsmojo, everybody else involved in the Loop driver for Omnipod and @jlucasvt from GetRileyLink.org
* `bolus advisor <../Configuration/Preferences.html#bolus-advisor>`_ & `eating reminder <../Getting-Started/Screenshots.html#eating-reminder>`_ @MilosKozak
* `New watchface <../Configuration/Watchfaces.html#new-watchface-as-of-androidaps-2-8>`_ @rICTx-T1D
* Dana RS connection improvements @MilosKozak
* Removed "Unchanged CGM values" behavior in SMB for Dexcom native app
* New `Low Ressolution Skin <../Configuration/Preferences.html#skin>`_
* New `"Pregnant" patient type <../Usage/Open-APS-features.html#overview-of-hard-coded-limits>`_ @Brian Quinion
* New NSClient tablet layout @MilosKozak
* NSClient transfer insulin, senstivity and display settings directly from main AAPS @MilosKozak
* `Preferences filter <../Configuration/Preferences.html>`_ @Brian Quinion
* New pump icons @Rig22 @@teleriddler @osodebailar
* New `insulin type Lyumjev <../Configuration/Config-Builder.html#lyumjev>`_
* SetupWizard improvements @MilosKozak
* Security improvements @dlvoy
* Various improvements and fixes @AdrianLxM @Philoul @swissalpine  @MilosKozak @Brian Quinion

Versión 2.7.0
================
Fecha de lanzamiento: 24-09-2020

**Make sure to check and adjust settings after updating to 2.7 as described** `here <../Installing-AndroidAPS/update2_7.html>`__.

You need at least start `objective 11 (in later versions objective 10!) <../Usage/Objectives.html#objective-10-automation>`_ in order to continue using `Automation feature <../Usage/Automation.html>`_ (all previous objectives must be completed otherwise starting Objective 11 is not possible). If for example you did not finish the exam in `objective 3 <../Usage/Objectives.html#objective-3-prove-your-knowledge>`_ yet, you will have to complete the exam before you can start `objective 11 <../Usage/Objectives.html#objective-10-automation>`_. This will not effect other objectives you have already finished. You will keep all finished objectives!

Nuevas características importantes
----------------------
* internal use of dependency injection, updates libraries, code rewritten to kotlin @MilosKozak @AdrianLxM
* using modules for Dana pumps @MilosKozak
* `new layout, layout selection <../Getting-Started/Screenshots.html>`_ @MilosKozak
* new `status lights layout <../Configuration/Preferences.html#status-lights>`_ @MilosKozak
* `multiple graphs support <../Getting-Started/Screenshots.html#section-f-main-graph>`_ @MilosKozak
* `Profile helper <../Configuration/profilehelper.html>`_ @MilosKozak
* visualization of `dynamic target adjustment <../Getting-Started/Screenshots.html#visualization-of-dynamic-target-adjustment>`_ @Tornado-Tim
* new `preferences layout <../Configuration/Preferences.html>`_ @MilosKozak
* SMB algorithm update @Tornado-Tim
* `Low glucose suspend mode <../Configuration/Preferences.html#aps-mode>`_ @Tornado-Tim
* `carbs required notifications <../Configuration/Preferences.html#carb-required-notification>`_ @twain47 @Tornado-Tim
* removed Careportal (moved to Actions) @MilosKozak
* `new encrypted backup format <../Usage/ExportImportSettings.html>`_ @dlvoy
* `new SMS TOTP authentication <../Children/SMS-Commands.html>`_ @dlvoy
* `new SMS PUMP CONNECT, DISCONNECT <../Children/SMS-Commands.html#commands>`_ commands @Lexsus
* better support for tiny basals on Dana pumps @Mackwe
* small Insight fixes @TebbeUbben @MilosKozak
* `"Default language" option <../Configuration/Preferences.html#general>`_ @MilosKozak
* vector icons @Philoul
* `set neutral temps for MDT pump <../Configuration/MedtronicPump.html#configuration-of-the-pump>`_ @Tornado-Tim
* History browser improvements @MilosKozak
* removed OpenAPS MA algorithm @Tornado-Tim
* removed Oref0 sensitivity @Tornado-Tim
* `Biometric or password protection <../Configuration/Preferences.html#protection>`_ for settings, bolus @MilosKozak
* `new automation trigger <../Usage/Automation.html>`_ @PoweRGbg
* `Open Humans uploader <../Configuration/OpenHumans.html>`_ @TebbeUbben @AdrianLxM
* New documentation @Achim

Versión 2.6.1.4
================
Fecha de lanzamiento: 04-05-2020

Please use `Android Studio 3.6.1 <https://developer.android.com/studio/>`_ or newer to build the apk.

Nuevas características importantes
----------------------
* Insight: Disable vibration on bolus for firmware version 3 - second attempt
* Otherwise is equal to 2.6.1.3. La actualización es opcional.

Versión 2.6.1.3
================
Fecha de lanzamiento: 03-05-2020

Please use `Android Studio 3.6.1 <https://developer.android.com/studio/>`_ or newer to build the apk.

Nuevas características importantes
------------------
* Insight: Disable vibration on bolus for firmware version 3
* Otherwise is equal to 2.6.1.2. La actualización es opcional.

Versión 2.6.1.2
================
Fecha de lanzamiento: 19-04-2020

Please use `Android Studio 3.6.1 <https://developer.android.com/studio/>`_ or newer to build the apk.

Nuevas características importantes
------------------
* Fix crashing in Insight service
* Otherwise is equal to 2.6.1.1. If you are not affected by this bug you don't need to upgrade.

Versión 2.6.1.1
================
Fecha de lanzamiento: 06-04-2020

Please use `Android Studio 3.6.1 <https://developer.android.com/studio/>`_ or newer to build the apk.

Nuevas características importantes
------------------
* Resolves SMS CARBS command issue while using Combo pump
* Otherwise is equal to 2.6.1. If you are not affected by this bug you don't need to upgrade.

Versión 2.6.1
==============
Fecha de lanzamiento: 21-03-2020

Please use `Android Studio 3.6.1 <https://developer.android.com/studio/>`_ or newer to build the apk.

Nuevas características importantes
------------------
* Allow to enter only ``https://`` in NSClient settings
* Fixed `BGI <../Getting-Started/Glossary.html>`_ displaying bug on watches
* Fixed small UI bugs
* Fixed Insight crashes
* Fixed future carbs with Combo pump
* Fixed `LocalProfile -> NS sync <../Configuration/Config-Builder.html#upload-local-profiles-to-nightscout>`_
* Insight alerts improvements
* Improved detection of boluses from pump history
* Fixed NSClient connection settings (wifi, charging)
* Fixed sending of calibrations to xDrip

Versión 2.6.0
==============
Fecha de lanzamiento: 29-02-2020

Please use `Android Studio 3.6.1 <https://developer.android.com/studio/>`_ or newer to build the apk.

Nuevas características importantes
------------------
* Small design changes (startpage...)
* Careportal tab / menu removed - more details `here <../Usage/CPbefore26.html>`__
* New `Local Profile plugin <../Configuration/Config-Builder.html#local-profile>`_

  * Local profile can hold more than 1 profile
  * Profiles can be cloned and edited
  * Ability of upload profiles to NS
  * Old profile switches can be cloned to new profile in LocalProfile (timeshift and percentage is applied)
  * Veritical NumberPicker for targets
* SimpleProfile is removed
* `Extended bolus <../Usage/Extended-Carbs.html#extended-bolus-and-switch-to-open-loop-dana-and-insight-pump-only>`_ feature - closed loop will be disabled
* MDT plugin: Fixed bug with duplicated entries
* Units are not specified in profile but it's global setting
* Added new settings to startup wizard
* Different UI and internal improvements
* `Wear complications <../Configuration/Watchfaces.html>`_
* New `SMS commands <../Children/SMS-Commands.html>`_ BOLUS-MEAL, SMS, CARBS, TARGET, HELP
* Fixed language support
* Objectives: `Allow to go back <../Usage/Objectives.html#go-back-in-objectives>`_, Time fetching dialog
* Automation: `allow sorting <../Usage/Automation.html#sort-automation-rules>`_
* Automation: fixed bug when automation was running with disabled loop
* New status line for Combo
* GlucoseStatus improvement
* Fixed TempTarget NS sync
* New statistics activity
* Allow Extended bolus in open loop mode
* Android 10 alarm support
* Tons on new translations

Versión 2.5.1
==================================================
Fecha de lanzamiento: 31-10-2019

Please note the `important notes <../Installing-AndroidAPS/Releasenotes.html#important-notes-2-5-0>`_ and `limitations <../Installing-AndroidAPS/Releasenotes.html#is-this-update-for-me-currently-is-not-supported>`_ listed for `version 2.5.0 <../Installing-AndroidAPS/Releasenotes.html#version-2-5-0>`__.
* Se corrigió un error en el receptor de estado de red que conduce a muchos fallos (no críticos, sino que desperdiciarían mucha energía en el recálculo de cosas).
* Nuevo mantenimiento de versiones que permitirá realizar actualizaciones menores sin activar la notificación de actualización.

Versión 2.5.0
==================================================
Fecha de lanzamiento: 26-10-2019

.. _important-notes-2-5-0:

Notas importantes
--------------------------------------------------
* Please use `Android Studio Version 3.5.1 <https://developer.android.com/studio/>`_ or newer to `build the apk <../Installing-AndroidAPS/Building-APK.html>`_ or `update <../Installing-AndroidAPS/Update-to-new-version.html>`_.
* Si está utilizando xDrip `identificar el receptor <../Configuration/xdrip.html#identify-receiver>`_ debe establecerse.
* If you are using Dexcom G6 with the patched Dexcom app you will need the version from the `2.4 folder <https://github.com/dexcomapp/dexcomapp/tree/master/2.4>`_.
* Glimp is supported from version 4.15.57 and newer.

¿Es esta actualización para mí? Actualmente NO es soportado
--------------------------------------------------
* Android 5 e inferiores
* Poctech
* 600SeriesUploader
* Dexcom Parchado desde el directorio 2.3

Nuevas características importantes
--------------------------------------------------
* Cambio interno de targetSDK a 28 (Android 9), soporte de jetpack
* Soporte de RxJava2, Okhttp3, Retrofit
* Viejo bombas "Medtronic" `Medtronic <../Configuration/MedtronicPump.html>`_ soporte (se necesita RileyLink)
* Nuevo " plugin de Automatización <../Usage/Automation.html>`_
* Allow to `bolus only part <../Configuration/Preferences.html#advanced-settings-overview>`_ from bolus wizard calculation
* Representación de la actividad de la insulina
* Adjusting IOB predictions by autosens result
* Nuevo soporte para los apks de Dexcom parcheados (` 2.4 carpeta <https://github.com/dexcomapp/dexcomapp/tree/master/2.4>`_)
* Verificador de firma
* Permite saltar objetivos para usuarios de OpenAPS
* Nuevos `objetivos <../Usage/Objectives.html>`_ - examinar, manejo de aplicaciones
  (Si ha iniciado al menos el objetivo "Iniciar en un lazo abierto" en las versiones anteriores, el examen es opcional.)
* Corregido el bug en controladores Dana* donde se informó una falsa diferencia de tiempo
* Se ha corregido el error en `SMS communicator <../Children/SMS-Commands.html>`_

Versión 2.3
==================================================
Fecha de lanzamiento: 25-04-2019

Nuevas características importantes
--------------------------------------------------
* Mejora de seguridad importante para Insight (realmente importante si se utiliza Insight!)
* Se corrigió el Historial
* Se corrigieron los cálculos delta
Actualización de idiomas
* Se verifica el GIT y se advierte sobre la actualización de gradle
* Más pruebas automáticas
* Arreglo de accidentes potenciales en el servicio AlarmSound (gracias a @lee-b!)
* Revisión de difusión de datos de BG (ahora funciona de forma independiente de los permisos de SMS!)
* Nuevo Verificador de Versiones


Versión 2.2.2
==================================================
Fecha de lanzamiento: 07-04-2019

Nuevas características importantes
--------------------------------------------------
* Arreglo de autosens: desactive el objetivo temporal de elevación/baja de TT
Nuevas traducciones
* Corrección de controladores de bomba Insight
* Arreglo de plug-in de SMS


Versión 2.2
==================================================
Fecha de lanzamiento: 29-03-2019

Nuevas características importantes
--------------------------------------------------
* `Arreglo DST <../Usage/Timezone-traveling.html#time-adjustment-daylight-savings-time-dst>`_
* Actualización de reloj
* `Plugin de SMS <../Children/SMS-Commands.html>`_ actualización
* Volver a los objetivos.
* Detener lazo si la memoria del teléfono está llena


Versión 2.1
==================================================
Fecha de lanzamiento: 03-03-2019

Nuevas características importantes
--------------------------------------------------
* `Accu-Chek Insight <../Configuration/Accu-Chek-Insight-Pump.html>`_ soporte (by Tebbe Ubben and JamOrHam)
* Luces de estado en la pantalla principal (Nico Schmitz)
* Horario de de verano (Roumen Georgiev)
* Arreglo de nombres de perfiles de NS (Johannes Mockenhaupt)
* Arreglo de Bloqueo de UI (Johannes Mockenhaupt)
* Soporte para la app actualizada del G5 (Tebbe Ubben y Milos Kozak)
* G6, Poctech, Tomate, Eversense BG soporte de origen (Tebbe Ubben y Milos Kozak)
* Se ha corregido la desactivación de SMB en preferencias (Johannes Mockenhaupt)

Misceláneo
--------------------------------------------------
* If you are using non default ``smbmaxminutes`` value you have to setup this value again


Versión 2.0
==================================================
Fecha de lanzamiento: 03-11-2018

Nuevas características importantes
--------------------------------------------------
* oref1/SMB support (`oref1 documentation <https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html>`_) Be sure to read the documentation to know what to expect of SMB, how it will behave, what it can achieve and how to use it so it can operate smoothly.
* `_Accu-Chek Combo <../Configuration/Accu-Chek-Combo-Pump.html>`_ soporte de la bomba
* Asistente de configuración: le guiará a través del proceso de configuración de AndroidAPS

Valores para ajustar cuando se cambia de AMA a SMB
--------------------------------------------------
* El objetivo 10 debe iniciarse para que las SMB estén habilitadas (la pestaña SMB muestra generalmente las restricciones que se aplican)
* maxIOB ahora incluye _all_ IOB, no sólo el basal añadido. Es decir, si se le da un bolo de 8 U para una comida y maxIOB es 7 U, no se entregarán SMB hasta que el IOB caiga por debajo de 7 U.
* El valor predeterminado de min_5m_carbimpact ha cambiado de 3 a 8 llendo de AMA a SMB. If you are upgrading from AMA to SMB, you have to change it manually
* Nota cuando se construya AndroidAPS 2.0 apk: La configuración personalizada no está soportada por la versión actual del plugin de Android Gradle! Si la compilación falla con un error en la configuración personalizada, puede realizar lo siguiente:

  * Abra la ventana de Preferencias, haga clic en Archivo > Configuración (en Mac, Android Studio > Preferencias).
  * En el panel de la izquierda, pulse Compilar, Ejecución, Deployment > Compilador.
  * Desmarque la casilla de verificación Configurar bajo demanda.
  * Haga clic en Aplicar o en Aceptar.

Pestaña general
--------------------------------------------------
* La cinta de arriba da acceso a suspensión/desactivación del lazo, ver/ajuste perfil y a inicio/detención de objetivos temporales (TTs). Los TTs utilizan los valores predeterminados establecidos en las preferencias. La nueva opción de Hypo TT es una temporal alta TT para evitar que el lazo haga una sobrecorrección muy agresiva en el rescate de carbohidratos.
* Botones de tratamiento: el botón de tratamiento viejo aún está disponible, pero está oculto de forma predeterminada. Ahora la visibilidad de los botones se puede configurar. Nuevo botón de insulina, nuevo botón de carbohidratos (incluyendo `eCarbs/carbs extendidos <../Usage/Extended-Carbs.html>`_)
* `Colored prediction lines <../Getting-Started/Screenshots.html#prediction-lines>`_
* Opción para mostrar un campo de notas en los diálogos de insulina/carbs/calculadora/cebado + relleno, que se suben a NS
* Actualizado el dialogo cebado/relleno permite el cebado y la creación de entradas para el careportal para el cambio de sitio y de cambio de los cartuchos

Reloj
--------------------------------------------------
* Se eliminó la variante de compilación separada, incluida en la compilación completa regular ahora. Para utilizar los controles de bolo desde el reloj, habilite este valor en el teléfono
* El asistente ahora sólo solicita carbohidratos (y el porcentaje si está habilitado en la configuración del reloj). Los parámetros que se incluyen en el cálculo se pueden configurar en la configuración del teléfono
* Las confirmaciones y los diálogos de información ahora funcionan también en el reloj 2.0
* Se añade Entrada de menú de eCarbs

Nuevos plugins
--------------------------------------------------
* PocTech app como fuente de BG
* Dexcom app parcheada como fuente BG
* Plugin de sensibilidad oref1

Misceláneo
--------------------------------------------------
* La aplicación ahora utiliza el cajón para mostrar todos los plugins; los plugins seleccionados como visibles en el creador de configuración se muestran como pestañas en la parte superior (favoritos)
* Revisión para las pestañas del constructor de configuración y objetivos, añadiendo descripciones
* Nuevo icono de la aplicación
* Muchas mejoras y correcciones de errores
* Nightscout-independent alerts if pump is unreachable for a longer time (e.g. depleted pump battery) and missed BG readings (see *Local alerts* in settings)
* Opción para mantener la pantalla encendida
* Opción de mostrar notificaciónes como notificación Android
* Filtrado avanzado (que permite siempre habilitar SMB y 6h después de las comidas) soportado con el app de Dexcom o xDrip patched con el modo nativo G5 como fuente BG.
