Примечания к изменениям в версиях
**************************************************
Пожалуйста, следуйте инструкциям по обновлению <../Installing-AndroidAPS/Update-to-new-version.html>`_. На ее страницах решаются наиболее распространенные проблемы связанные с обновлениями.

Как только будет доступно новое обновление вы получите следующую информацию:

.. изображение: ../images/AAPS_LoopDisable90days.png
  :alt: Информация об обновлении

У вас есть 60 дней для обновления. Если вы не обновитесь в течение 60 дней AAPS войдет в режим LGS (приостановка на низких ГК - см.`glossary <../Getting-Started/Glossary.html>`_) as in `objective 6 <../Usage/Objectives.html>`_.
ContextEdit.

Если вы не обновитесь еще 30 дней (90 дней с новой даты выпуска) AAPS переключится в режим открытого цикла.

Имейте в виду, что это изменение не предназначено для того, чтобы действовать вам на нервы, а существует по соображениям безопасности. Новые версии AndroidAPS не только обеспечивают новые возможности, но и содержат исправления безопасности. Поэтому необходимо, чтобы каждый пользователь обновлял приложение как можно чаще.. К сожалению, все еще поступают сообщения об ошибках из очень старых версий, поэтому это попытка повысить безопасность каждого пользователя и всего сообщества. Благодарим за понимание!

Версия Android и версия AAPS
====================================
Если ваш смартфон использует версию Android до Android 9, вы не сможете использовать AAPS 3.. 0 и выше, так как она требует не ниже Android 9.

Чтобы пользователи более старой версии Android могли применять старые версии AAPS для них была изменена только проверка версий. Никаких других улучшений не включено.

Android 9 и выше
------------------------------------
Пользуйтесь новейшей версией AAPS
Загрузите код AAPS здесь https://github.com/nightscout/AndroidAPS

Android 8
------------------------------------
* Пользуйтесь AAPS версии **2.8.2.1**
* Download AAPS Code from https://github.com/nightscout/AndroidAPS branch 2.8.2.1

Android 7
------------------------------------
* Пользуйтесь AAPS версии **2.6.2**
* Download AAPS Code from https://github.com/nightscout/AndroidAPS branch 2.6.2

Version 3.1.0
================
Release date: XX-XX-2022

Важные Примечания
----------------------
* after update uninstall Wear app and install new version
* Omnipod users: update on pod change

Изменения
----------------------
* fixed issues from 3.0 version
* fix application freezing @MilosKozak
* fixed DASH driver @avereha
* fixed Dana drivers @MilosKozak
* huge UI improvement, cleanup and unification, migration to material design, styles, white theme, new icons. @Andries-Smit @MilosKozak @osodebailar @Philoul
* widget @MilosKozak
* Aidex CGM support @andyrozman @markvader (Pumpcontrol only)
* Wear tiles, translations @Andries-Smith
* Wear code refactored. Not backward compatible anymore @MilosKozak
* a11y improvements @Andries-Smith
* new protection option PIN @Andries-Smit
* allow graph scale from menu @MilosKozak
* more statistics available @MilosKozak
* MDI plugin removed in favor of VirtualPump

Version 3.0.0
================
Release date: 31-01-2022

Важные подсказки
----------------------
* **Минимальная версия Android теперь 9.0**
* **Данные не переносятся в новую базу данных.** Не жалуйтесь, это практически невозможно. Таким образом после обновления данные IOB, COB, терапии и т. д. будут очищены. You have to create new `profile switch <../Usage/Profiles.html>`_ and start with zero IOB and COB. Планируйте обновление тщательно!!! Лучшая ситуация - без активного инсулина и углеводов
* Используйте одну версию AAPS и NSClient

**Make sure to check and adjust settings after updating to 3.0 as described** `here <../Installing-AndroidAPS/update3_0.html>`__.

Этапы подготовки
----------------------
**At least two days before update:**

* отключите Dexcom bridge в Nightscout
* if you are using G5/G6 and xDrip as a collector, you have to update xDrip to a nightly version newer than 14th January 2022
* if you are using G5/G6 switching to BYODA as collector is recommended to take advantage of back-smoothing (you can still use xDrip for other purposes, xDrip can receive data from BYODA)


Изменения
----------------------
* 100k lines changed, 105k new lines of code
* `Omnipod DASH support <../Configuration/OmnipodDASH.html>`_ @AdrianLxM @avereha @bartsopers @vanelsberg
* `Поддержка Dana-i <../Configuration/DanaRS-Insulin-Pump.html>`_ @MilosKozak
* `DiaconnG8 support <../Configuration/DiaconnG8.html>`_
* Поддержка Glunovo
* Внутренняя база данных обновлена до Room @MilosKozak @Tebbe @AdrianLxm @Philoul @andyrozman
* Часть кода переписана на Kotlin @MilosKozak
* Новый интерфейс для драйверов помп
* NSClient переписан для лучшей синхронизации и более детальной настройки @MilosKozak

  * Удаление записи из NS не допускается (аннулирование только через NSClient)
  * Модификация записи из NS не допускается
  * Доступны настройки синхронизации без перехода в инженерный режим (для родителей)
  * Возможность повторной синхронизации данных

* Изменение поведения смены профиля. Теперь имеется различие между Переключением Профилей *(чего хочет пользователь)* и Изменением Профиля *(когда изменение инициируется помпой)* @MilosKozak @Tebbe
* Можно начать выполнение временной цели при создании переключателя профиля @MilosKozak
* NSProfile is gone, just local profile can be used. Local profile can be `synced to NS <../Installing-AndroidAPS/update3_0.html#nightscout-profile-cannot-be-pushed>`_. @MilosKozak.
* Forgotten `master password reset procedure <../Installing-AndroidAPS/update3_0.html#reset-master-password>`_ @MilosKozak
* Отслеживание действий пользователя @Philoul
* Новый триггер автоматизации - значение временной цели - TempTargetValue @Philoul
* New automation Careportal action @Philoul
* Add Bolus reminder in Carbs Dialog @Philoul
* Bolus Wizard improvement
* Улучшения пользовательского интерфейса @MilosKozak
* Новые пользовательские кнопки для автоматизации @MilosKozak
* Новый макет автоматизации @MilosKozak
* Браузер истории обновлён и исправлен @MilosKozak
* Цель 9 удалена @MilosKozak
* Исправлена ошибка, связанная с нестабильными данными CGM @MilosKozak
* Улучшение связи с DanaR и DanaRS @MilosKozak
* Интеграция с CircleCI @MilosKozak
* Files location change:

   * /AAPS/extra (engineering mode)
   * /AAPS/logs /AAPS/exports
   * /AAPS/preferences

Версия 2.8.2
================
Дата выпуска: 23-01-2021

* См. также `important hints for version 2.8.1.1 <../Installing-AndroidAPS/Releasenotes.html#important-hints>`_ ниже.

Изменения
----------------------
* Улучшения стабильности
*больше подстроек для Android 8+
* улучшенные иконки
* улучшения для смарт-часов
* Исправления для NSClient
*Помощник болюса теперь работает с Pumpcontrol и NSClient

Версия 2.8.1.1
================
Дата выпуска: 12-01-2021

Важные Примечания
----------------------
* Параметр **NS_UPLOAD_ONLY** (только загрузка в NS) был принудительно включен для всех пользователей 2.8.1.
* Если вы используете NSClient для ввода временных целей TT, углеводов или профилей вы должны отключить его в AAPS, но **только в том случае, если ваша синхронизация хорошо работает** (т. е. вы не видите нежелательных вариаций в данных, таких как произвольное самоизменение TT, TBR и т. д.).
* ВНИМАНИЕ: НЕ делайте это, если есть какие-либо другие методы обработки (например, трансляция и загрузка/синхронизация xDrip...).
* NS_UPLOAD_ONLY может быть выключен только в инженерном режиме.

Основные изменения
----------------------
* улучшения и исправления RileyLink, помпы Omnipod и подачи инсулина шприц-ручками
* принудительный режим загрузки в NS NS_UPLOAD_ONLY
* исправления SMB и приложения Dexcom
* Исправления циферблатов смарт-часов
* улучшена отчетность о сбоях
* понижена версия системы автоматической сборки gradle для разрешения прямой установки приложения на смарт-часы
* Исправления автоматизации
* Улучшение работы драйвера помпы Dana RS
* исправлен ряд сбоев
* Исправления и улучшения интерфейса
* новые переводы

Версия 2.8.0
================
Дата выпуска: 01-01-2021

Важные Примечания
----------------------
* **Минимальная версия теперь Android 8.0.** Для более старых версий Android, все еще можно использовать 2.6.1.4 в старом репозитории.
* «Цели претерпели изменения. <../Usage/Objectives.html#objective-3-prove-your-knowledge>`_ **Завершите выполнение целей до обновления.**
* Расположение репозитория https://github.com/nightscout/AndroidAPS . Если вы не знакомы с Git самый простой способ обновления- удалить каталог с AndroidAPS и `заново клонировать <../Installing-AndroidAPS/Building-APK.html>`_.
* Используйте ` Android Studio 4.1.1 <https://developer.android.com/studio/>` _ или новее, чтобы построить apk.

Новые возможности
----------------------
* `Поддержка Omnipod Eros <../Configuration/OmnipodEros. tml>`_ @bartsopers @andyrozman @ktomy @samspycher @TeleRiddler @vanelsberg @eurenda and special thanks to @ps2 @itsmojo, все остальные, участвующие в разработке драйвера для Omnipod а также @jlucasvt с GetRileyLink.org
* `помощник болюса <../Configuration/Preferences.html#bolus-advisor>`_ & `подсказка о приеме пищи <../Getting-Started/Screenshots.html#eating-reminder>`_ @MilosKozak
* `Новый циферблат смарт-часов <../Configuration/Watchfaces.html#new-watchface-as-of-androidaps-2-8>`_ @rICTx-T1D
* Улучшение связи с Dana RS @MilosKozak
* Удален алгоритм "Неизмененные значения CGM " в SMB для оригинального приложения Dexcom
* Новый скин `Низкое разрешение <../Configuration/Preferences.html#skin>`_
* Новый `тип пациента "Беременные" <../Usage/Open-APS-features.html#overview-of-hard-coded-limits>`_ @Brian Quinion
* Новый макет вкладки NSClient @MilosKozak
* Передача данных об инсулине, чувствительности и настройках отображения непосредственно с приложения AAPS @MilosKozak
* `Фильтр параметров конфигурации <../Configuration/Preferences.html> ` _ @Brian Quinion
* Новые иконки помп @Rig22 @@teleriddler @osodebailar
* Новый тип инсулина `Lyumjev <../Configuration/Config-Builder.html#lyumjev>`_
* Улучшения Помощника настройки @MilosKozak
* Улучшения безопасности @dlvoy
* Различные улучшения и исправления @AdrianLxM @Philoul @swissalpine @MilosKozak @Brian Quinion

Версия 2.7.0
================
Дата выпуска: 24-09-2020

**Не забудьте проверить и исправить настройки после обновления до 2.7, описание см. ** `здесь <../Installing-AndroidAPS/update2_7.html>`__.

You need at least start `objective 11 (in later versions objective 10!) <../Usage/Objectives.html#objective-10-automation>`_ in order to continue using `Automation feature <../Usage/Automation.html>`_ (all previous objectives must be completed otherwise starting Objective 11 is not possible). If for example you did not finish the exam in `objective 3 <../Usage/Objectives.html#objective-3-prove-your-knowledge>`_ yet, you will have to complete the exam before you can start `objective 11 <../Usage/Objectives.html#objective-10-automation>`_. Это не повлияет на другие цели, которые вы уже выполнили. У вас сохранятся все завершенные цели!

Новые возможности
----------------------
* внутреннее использование зависимостей инъекций, библиотеки обновлений, код переписан на kotlin @MilosKozak @AdrianLxM
* применение модулей для помп Dana @MilosKozak
* `новый макет, выбор макета <../Getting-Started/Screenshots.html>`_ @MilosKozak
* новый вид индикаторов состояния <../Configuration/Preferences.html#status-lights>`_ @MilosKozak
* `Поддержка нескольких графиков <../Getting-Started/Screenshots.html#section-f-main-graph>`_ @MilosKozak
* `Помощник профиля а <../Configuration/profilehelper.html>`_ @MilosKozak
* визуализация динамического изменения целевого показателя <../Getting-Started/Screenshots.html#visualization-of-dynamic-target-adjustment>`_ @Tornado-Tim
* новый макет параметров конфигурации <../Configuration/Preferences.html>`_ @MilosKozak
* Обновление алгоритма микроболюсов SMB @Tornado-Tim
* `Режим приостановки при низкой гликемии <../Configuration/Preferences.html#aps-mode>`_ @Tornado-Tim
Уведомления о потребности в углеводах <../Configuration/Preferences.html#carb-required-notification>`_ @twain47 @Tornado-Tim
* удален портал терапии Careportal (перемещен в Actions) @MilosKozak
* `новый формат зашифрованной резервной копии <../Usage/ExportImportSettings.html>`_ @dlvoy
* `новая верификация SMS TOTP <../Children/SMS-Commands.html>`_ @dlvoy
* `новые команды SMS PUMP CONNECT, DISCONNECT <../Children/SMS-Commands.html#commands>`_@Lexsus
* улучшена поддержка микро базалов на помпах Dana @Mackwe
* небольшие исправления для помпы Insight @TebbeUbben @MilosKozak
* `"Язык по умолчанию" <../Configuration/Preferences.html#general>`_ @MilosKozak
* векторные иконки @Philoul
* `set neutral temps for MDT pump <../Configuration/MedtronicPump.html#configuration-of-the-pump>`_ @Tornado-Tim
* Улучшения в браузере истории @MilosKozak
* удалён алгоритм OpenAPS MA @Tornado-Tim
* Удалена чувствительность Oref0 @Tornado-Tim
* `Биометрическая защита или защита паролем <../Configuration/Preferences.html#protection>`_ для настроек, болюсов @MilosKozak
* `новый триггер автоматизации <../Usage/Automation.html>`_ @PoweRGbg
* `выгрузка в Open Humans <../Configuration/OpenHumans.html>`_ @TebbeUbben @AdrianLxM
* Новая документация @Achim

Версия 2.6.1.4
================
Дата выпуска: 04-05-2020

Используйте ` Android Studio 3.6.1 <https://developer.android.com/studio/>` _ или новее, чтобы построить apk.

Новые возможности
----------------------
* Insight: Выключение вибрации при болюсах на версии прошивки 3-вторая попытка
* В остальном эквивалентна 2.6.1.3. Обновление не является обязательным.

Версия 2.6.1.3
================
Дата выпуска: 03-05-2020

Используйте ` Android Studio 3.6.1 <https://developer.android.com/studio/>` _ или новее, чтобы построить apk.

Новые возможности
------------------
* Insight: Выключение вибрации при болюсах на версии прошивки 3
* В остальном эквивалентна 2.6.1.2. Обновление не является обязательным.

Версия 2.6.1.2
================
Дата выпуска: 19-04-2020

Используйте ` Android Studio 3.6.1 <https://developer.android.com/studio/>` _ или новее, чтобы построить apk.

Новые возможности
------------------
* Исправлен сбой в службе Insight
* В остальном эквивалентна 2.6.1.1. Если эта ошибка не влияет на вас, обновление не требуется.

Версия 2.6.1.1
================
Дата выпуска: 06-04-2020

Используйте ` Android Studio 3.6.1 <https://developer.android.com/studio/>` _ или новее, чтобы построить apk.

Новые возможности
------------------
* Исправлена ошибка команды SMS CARBS при использовании помпы Combo
* В остальном эквивалентна 2.6.1. Если эта ошибка не влияет на вас, обновление не требуется.

Версия 2.6.1
==============
Дата выпуска: 21-03-2020

Используйте ` Android Studio 3.6.1 <https://developer.android.com/studio/>` _ или новее, чтобы построить apk.

Новые возможности
------------------
* Возможность вводить только "https:// в настройках NSClient
* Исправлено ` BGI <../Getting-Started/Glossary.html> ` _ отображение ошибок в часах
* Исправлены мелкие ошибки интерфейса
* Исправлены сбои Insight
* Исправлены углеводы в будущем с помпой Combo
* Исправленo LocalProfile -> NS sync <../Configuration/Config-Builder.html#upload-local-profiles-to-nightscout>`_
* Улучшения оповещений Insight
* Улучшено обнаружение болюсов в истории помпы
* Исправлены параметры соединения NSClient (wifi, зарядка)
* Исправлена отправка калибровок в xDrip

Версия 2.6.0
==============
Дата выпуска: 29-02-2020

Используйте ` Android Studio 3.6.1 <https://developer.android.com/studio/>` _ или новее, чтобы построить apk.

Новые возможности
------------------
* Небольшие изменения дизайна (стартовая страница...)
* Удалена закладка / меню Careportal - подробнее `здесь <../Usage/CPbefore26.html>`__
* New `Local Profile plugin <../Configuration/Config-Builder.html#local-profile>`_

  * Локальный профиль может иметь более 1 профиля
  * Профили можно копировать и редактировать
  * Возможность загружать профили на NS
  * Старые переключатели профиля можно клонировать на новый в LocalProfile (применяется сдвиг по времени и процент)
  * Vertical NumberPicker для целей
* SimpleProfile удален
* `Extended bolus <../Usage/Extended-Carbs.html#extended-bolus-and-switch-to-open-loop-dana-and-insight-pump-only>`_ feature - closed loop will be disabled
* Плагин MDT: Исправлена ошибка с дублирующимися записями
* Единицы не указаны в профиле, но это глобальные параметры
* Добавлены новые параметры для мастера установки
* Измененный пользовательский интерфейс и внутренние улучшения
* `Усложнения Wear <../Configuration/watchfaces.html>`_
* Новые `SMS команды <../Children/SMS-Commands.html>`_ BOLUS-MEAL, SMS, CARBS, TARGET, HELP
* Исправлена поддержка языков
* Цели: позволяют вернуться <../использования/цели.диалоговое окно HTML#идем-назад-в-задачах>`_,выбор времени
* Автоматизация: ` позволяет сортировку <../Usage/Automation.html#sort-automation-rules> ` _
* Автоматизация: исправляется ошибка, когда автоматизация выполнялась с отключенным циклом
* Новая строка состояния для Combo
* Улучшенное состояние ГК
* Исправлена синхронизация врем целей с NS
* Новая статистика
* Разрешен пролонгированный болюс в режиме открытого цикла
* Поддержка оповещений Android 10
* Тонны новых переводов

Версия 2.5.1
==================================================
Дата выпуска: 31-10-2019

Обратите внимание на " важные примечания <../Installing-AndroidAPS/Releasenotes.html#important-notes-2-5-0>`_ and `limitations <../Installing-AndroidAPS/Releasenotes.html#is-this-update-for-me-currently-is-not-supported>`_ listed for `version 2.5.0 <../Installing-AndroidAPS/Releasenotes.html#version-2-5-0>`__.
* Исправлена ошибка в сетевом состоянии, которые приводят к ошибкам (не критично, но будет тратить много энергии на пересчет).
* Новая иерархия версий, позволяющая выполнять незначительные обновления без уведомлений об обновлении.

Версия 2.5.0
==================================================
Дата выпуска: 26-10-2019

.. Важные замечания -2-5-0:

Важные замечания
--------------------------------------------------
* Пожалуйста, используйте `Android Studio версии 3.5.1 <https://developer.android.com/studio/>`_ или новее, чтобы `собрать apk <../Installing-AndroidAPS/Building-APK.html>`_ или `update <../Installing-AndroidAPS/Update-to-new-version.html>`_.
* Если вы используете xDrip, должен быть отмечен `identify receiver <../Configuration/xdrip.html#identify-receiver>`_.
* If you are using Dexcom G6 with the patched Dexcom app you will need the version from the `2.4 folder <https://github.com/dexcomapp/dexcomapp/tree/master/2.4>`_.
* Поддержка Glimp версии 4.15.57 и новее.

Это обновление для меня? В настоящее время НЕ поддерживается
--------------------------------------------------
* Android 5 и ниже
* Poctech
* 600SeriesUploader
* Модифицированное приложение Dexcom из каталога 2.3

Новые возможности
--------------------------------------------------
* Внутреннее изменение targetSDK на 28 (Android 9), поддержка jetpack
* Поддержка RxJava2, Okhttp3, Retrofit
*Поддержка старых помп `Medtronic <../Configuration/MedtronicPump.html>`_ поддержка (нужен RileyLink)
* Новый модуль `Автоматизация <../Usage/Automation.html>`_
* Позволяет подать `только часть болюса <../Configuration/Preferences.html#advanced-settings-overview>`_ с калькулятора болюса
* Рендеринг активности инсулина
* Корректировка прогнозов IOB с помощью результата autosense
Новая поддержка модифицированных приложений Dexcom (<https://github.com/dexcomapp/dexcomapp/tree/master/2.4> папка 2.4)
* Верификатор подписи
* Возможность обойти цели пользователям OpenAPS
* Новые цели <../Usage/Objectives.html> ` _-экзамен, обработка приложений
  (Если вы начали хотя бы цель "открытый цикл" в предыдущих версиях экзамен не является обязательным.)
* Исправлена ошибка в драйверах Dana*, где сообщалось о ложной разнице во времени
* Исправлена ошибка в `SMS коммуникаторе <../Children/SMS-Commands.html>`_

Версия 2.3
==================================================
Дата выпуска: 25-04-2019

Новые возможности
--------------------------------------------------
* Важное исправление безопасности для Insight (очень важно, если вы используете Insight!)
* Исправлен браузер истории
* Исправление расчетов дельты
* Обновление переводов
* Проверка GIT и предостережение об обновлении gradle
* Больше автоматического тестирования
* Исправление потенциального сбоя в службе AlarmSound (спасибо @lee-b !)
* Исправлена передача данных ГК (теперь работает независимо от разрешения SMS!)
* Новый модуль проверки версий


Версия 2.2.2
==================================================
Дата выпуска: 07-04-2019

Новые возможности
--------------------------------------------------
* Исправление Autosens: деактивировать значение временная цель ТТ повышает/понижает целевое значение
* Новые переводы
* Исправления драйверов Insight
* исправление модуля SMS


Версия 2.2
==================================================
Дата выпуска: 29-03-2019

Новые возможности
--------------------------------------------------
* `Исправление ошибки летнего времени <../Usage/Timezone-traveling.html#time-adjustment-daylight-savings-time-dst>`_
ContextEdit
* Обновление Wear
* ` Модуль SMS <../Children/SMS-Commands.html> ` _ обновление
* Возможность возврата к предыдущим целям.
* Остановка цикла, если память телефона заполнена


Версия 2.1
==================================================
Дата выпуска: 03-03-2019

Новые возможности
--------------------------------------------------
* `Поддержка Аccu-Chek Insight <../Configuration/Accu-Chek-Insight-Pump.html>'_(от Tebbe Ubben и JamOrHam)
* Индикаторы состояния на главном экране (Nico Schmitz)
* Помощник перехода на летнее время (Румен Георгиев)
* Исправлеие обработки имен профилей, поступивших от NS (Johannes Mockenhaupt)
* Исправление блокировки интерфейса (Johannes Mockenhaupt)
* Поддержка обновленного приложения G5 (Tebbe Ubben и Milos Kozak)
* Поддержка G6, Poctech, Tomato, Eversense BG (Tebbe Ubben и Milos Kozak)
* Исправлено отключение SMB в настройках (Johannes Mockenhaupt)

Разное
--------------------------------------------------
* Если вы задавали собственное значение smbmaxminutes, нужно заново его настроить


Версия 2.0
==================================================
Дата выпуска: 03-11-2018

Новые возможности
--------------------------------------------------
* Поддержка oref1/SMB (<https://openaps.readthedocs.io/en/latest/docs/Customize-Iterate/oref1.html>документация oref1). Обязательно прочтите документацию, чтобы знать, чего ожидать от SMB, как он себя поведет, чего может достичь и как добиться его ровной работы.
* ` _Accu-Chek Combo <../Configuration/Accu-Chek-Combo-Pump.html> ` _ Поддержка помпы
* Мастер установки: направляет вас через процесс настройки AndroidAPS

Настройки при переключении с AMA на SMB
--------------------------------------------------
* Для включения SMB необходимо начать выполнение цели 10 (вкладка SMB обычно показывает какие применяются ограничения)
* maxIOB теперь включает весь IOB, а не только добавленный базал. То есть, если дан болюс 8 ед. на еду a максимальный IOB ограничен 7 ед., то SMB не будет подан до тех пор, пока активный инсулин IOB не опустится ниже 7 ед.
* минимальное воздействие углеводов min_5m_carbimpact по умолчанию изменилось с 3 до 8, при переходе с AMA на SMB. Если вы переходите с AMA к SMB, то вам нужно изменить его вручную
* Обратите внимание при создании приложения AndroidAPS 2.0: Выборочная Конфигурация не поддерживается текущей версией плагина Android Gradle! Если сборка выполнена с ошибкой, относящейся к "выборочной конфигурации", можно сделать следующее:

  * Откройте окно настроек, нажав Файл > Настройки (на Mac, Android Studio > Настройки).
  * В левой панели нажмите Сборка, Выполнение, Развертывание > Компилятор.
  Снимите флажок с ячейки "выборочная конфигурация".
  * Нажмите Применить или OK.

Вкладка обзора
--------------------------------------------------
* Верхняя полоса дает доступ к приостановке/отключению цикла, просмотру/настройке профиля и запуску/остановке временных целей (TT). Временные цели TT используют настройки по умолчанию. Новая опция Гипо TT является высокой временной целью TT для предотвращения слишком агрессивной реакции на корректирующие углеводы.
* Кнопки терапии: старая кнопка все еще доступна, но скрыта по умолчанию. Видимость кнопок теперь может быть сконфигурирована. Новая кнопка инсулина, новая кнопка (включая ` eCarbs/extended carbs <../Usage/Extended-Carbs.html> ` _)
* `Цветные линии прогнозирования <../Getting-Started/Screenshots.html#section-e>`_
* Опция отображения поля заметок об инсулине/углеводах/калькуляторе/первичном заполнении которые передаются в NS
* Обновленное диалоговое окно «первичное/заполнение» позволяет заполнять инфузионный набор и вносить данные об изменении места установки и замене картриджа

Часы
--------------------------------------------------
* Отдельный вариант сборки изъят, теперь включен в регулярную полную сборку. Чтобы иметь управления болюсами с часов, включите этот параметр на телефоне
* Мастер теперь запрашивает только углеводы (и процент, если он включен в настройках часов). То, какие параметры входят в расчет можно задать в настройках телефона
* диалоги подтверждения и информирования теперь работают и на wear 2.0
* Добавлена запись меню eCarbs

Новые расширения
--------------------------------------------------
* Приложение PocTech в качестве источника данных ГК
* Измененное приложение Dexcom как источник ГК
* плагин чувствительности oref1

Разное
--------------------------------------------------
* Приложение теперь использует меню для отображения расширений; плагины, выбранные как видимые в конфигураторе, показаны как вкладки сверху (избранное)
* Переработан конфигуратор и вкладки целей, добавлены описания
* Новый значок приложения
* Много улучшений и исправлений
* независимые от Nightscout оповещения, если помпа недоступна длительное время (например, севшая батарея помпы) и пропущенные показания ГК (см. _Локальные оповещения _ в настройках)
* Возможность держать экран включенным
* Опция отображения уведомлений как уведомление Android
* Расширенная фильтрация (позволяющая всегда включать SMB и на 6час. после еды) поддерживаемая модифицированным приложением Dexcom или xDrip в нативном режиме G5 в качестве источника ГК.
