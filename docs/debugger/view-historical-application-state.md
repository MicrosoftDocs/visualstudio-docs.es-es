---
title: Visualización del estado anterior de la aplicación con IntelliTrace
description: Obtenga información sobre cómo tomar instantáneas y verlas con step-back de IntelliTrace
ms.custom: seodec18
ms.date: 09/19/2018
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1ab54ccb3820b3a03724c30d16f08b3e8a45493
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933107"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio-visual-studio-enterprise"></a>Inspección de los estados de aplicación anteriores mediante el retroceso de IntelliTrace en Visual Studio (Visual Studio Enterprise)

La característica step-back (paso atrás) de IntelliTrace toma automáticamente una instantánea de la aplicación en cada punto de interrupción y evento de paso del depurador. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

La característica step-back de IntelliTrace está disponible a partir de Visual Studio Enterprise 2017 versión 15.5 y versiones posteriores, y requiere Windows 10 Anniversary Update o posterior. La característica se admite actualmente para la depuración de ASP.NET, WinForms, WPF, aplicaciones de consola administrada y bibliotecas de clases administradas. A partir de Visual Studio Enterprise 2017 versión 15.7, también se admite la característica de ASP.NET Core y .NET Core. A partir de Visual Studio Enterprise 2017 versión 15.9 versión preliminar 2, también se admite la característica para aplicaciones nativas dirigidas a Windows. No se admite la depuración de aplicaciones de UWP actualmente.

En este tutorial va a:

> [!div class="checklist"]
> * Activación de las instantáneas y los eventos de IntelliTrace
> * Navegar por los eventos mediante los comandos Retroceder paso a paso y Avanzar paso a paso
> * Ver las instantáneas de eventos

## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Activar eventos de IntelliTrace y el modo instantáneas

1. Abra el proyecto en Visual Studio Enterprise.

1. Abra la configuración **Herramientas** > **Opciones** > **IntelliTrace** y seleccione la opción **Eventos e instantáneas de IntelliTrace**.

    A partir de Visual Studio 2017 Enterprise versión 15.9 versión preliminar 2, esta opción es **Instantáneas de IntelliTrace (administradas y nativas)** .

    ![Activar eventos de IntelliTrace y el modo instantáneas](../debugger/media/intellitrace-enable-snapshots.png "Activar eventos de IntelliTrace y el modo instantáneas")

1. Si desea configurar las opciones para ver instantáneas en excepciones, elija **IntelliTrace** > **Avanzadas** en el cuadro de diálogo **Opciones**.

    Estas opciones están disponibles a partir de Visual Studio Enterprise 2017 versión 15.7.

    ![Configurar el comportamiento de las instantáneas en excepciones](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Al habilitar eventos e instantáneas, tomar instantáneas en excepciones está también habilitado de forma predeterminada. Para deshabilitar las instantáneas en excepciones, anule la selección de **Recopilar instantáneas en los eventos de excepción**. Cuando esta característica está habilitada, se toman instantáneas en las excepciones no controladas. En las excepciones administradas, se toman instantáneas solo si se produce la excepción y si no se vuelve a producir una excepción iniciada anteriormente. Puede establecer un número máximo de instantáneas en excepciones seleccionando un valor de la lista desplegable. El valor máximo se aplica por cada vez que la aplicación entra en modo de interrupción (por ejemplo, cuando la aplicación alcanza un punto de interrupción).

    > [!NOTE]
    > Las instantáneas se toman solo para eventos de excepción que IntelliTrace registre. Para código administrado, haga clic en **Herramientas** > **Opciones** > **Eventos de IntelliTrace** para especificar qué eventos registra IntelliTrace.

1. En el proyecto, establezca uno o varios puntos de interrupción e inicie la depuración (presione **F5**), o inicie la depuración pasando por el código (**F10** o **F11**).

    IntelliTrace toma una instantánea del proceso de la aplicación en cada paso del depurador, eventos de punto de interrupción y eventos de excepción no controlados. Estos eventos se registran en la pestaña **Eventos** de la ventana **Herramientas de diagnóstico**, junto con otros eventos de IntelliTrace. Para abrir esta ventana, elija **Depurar** > **Windows** > **Mostrar herramientas de diagnóstico**.

    Aparece un icono de cámara junto a los eventos para los que hay instantáneas.

    ![Pestaña Eventos con instantáneas](../debugger/media/intellitrace-events-tab-with-snapshots.png "Pestaña Eventos con instantáneas en los puntos de interrupción y los pasos")

    Por motivos de rendimiento, no se toman instantáneas paso a paso muy rápidamente. Si no aparece ningún icono de cámara junto al paso, intente ejecutar más lentamente.

## <a name="navigate-and-view-snapshots"></a>Navegar y ver instantáneas

1. Para navegar por los eventos, use los botones **Retroceder paso a paso (Alt + [)** y **Avanzar paso a paso (Alt + ])** en la barra de herramientas Depuración.

    Estos botones permiten navegar por los eventos que aparecen en la pestaña **Eventos** de la **ventana Herramientas de diagnóstico**. Retroceder o avanzar paso a paso a un evento activa de manera automática la [depuración histórica](../debugger/historical-debugging.md) del evento seleccionado.

    ![Botones Retroceder paso a paso y Avanzar paso a paso](../debugger/media/intellitrace-step-back-icons-description.png "Botones Retroceder paso a paso y Avanzar paso a paso")

    Al retroceder o avanzar paso a paso, Visual Studio entra en modo de depuración histórica. En este modo, el contexto del depurador cambia a la hora a la que se registró el evento seleccionado. Visual Studio también mueve el puntero a la línea de código correspondiente en la ventana de código fuente.

    Desde esta vista, puede inspeccionar los valores de las ventanas **Pila de llamadas**, **Variables locales**, **Automático** e **Inspección**. También puede mantener el mouse sobre las variables para ver información sobre datos y realizar la evaluación de expresiones en la ventana **Inmediato**. Los datos que ve provienen de la instantánea del proceso de la aplicación que se realizó en ese momento dado.

    Así, por ejemplo, si ha alcanzado un punto de interrupción y realizado un Paso (**F10**), el botón **Retroceder paso a paso** pone a Visual Studio en el modo histórico en la línea de código correspondiente al punto de interrupción.

    ![Activar el modo histórico en un evento con una instantánea](../debugger/media/intellitrace-historical-mode-with-snapshot.png "Activar el modo histórico en un evento con una instantánea")

2. Para volver a la ejecución en vivo, elija **Continuar (F5)** o haga clic en el vínculo **Volver a depuración en directo** en la barra de información.

3. También puede ver una instantánea de la pestaña **Eventos**. Para ello, seleccione un evento con una instantánea y haga clic en **Activar depuración histórica**.

    ![Activar depuración histórica en un evento](../debugger/media/intellitrace-activate-historical-debugging.png "Activar depuración histórica en un evento")

    A diferencia del comando **Establecer instrucción siguiente**, ver una instantánea no vuelve a ejecutar el código; en su lugar, le proporciona una vista estática del estado de la aplicación en un punto en el tiempo que se ha producido en el pasado.

    ![Información general de step-back de IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "Información general de Step-back de IntelliTrace")

    Para más información sobre cómo inspeccionar variables en Visual Studio, consulte [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>¿Qué diferencia hay entre el modo solo de eventos de IntelliTrace y la característica step-back?

IntelliTrace en modo de solo eventos permite activar la depuración histórica en puntos de interrupción y pasos del depurador. Sin embargo, IntelliTrace solo captura los datos en las ventanas **Variables locales** y **Automático** si están abiertas y solo captura los datos que están expandidos y en la vista. En modo de solo los eventos, a menudo no tiene una visión completa de las variables y los objetos complejos. Además, la evaluación de expresiones y la visualización de datos en la ventana **Inspección** no es compatible.

En los modos de eventos y de instantáneas, IntelliTrace captura la instantánea completa del proceso de la aplicación, incluidos los objetos complejos. En una línea de código, puede ver la misma información como si se hubiese detenido en un punto de interrupción (y no importa si anteriormente se expandió la información). La evaluación de expresiones también se admite cuando se está viendo una instantánea.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>¿Cuál es el impacto en el rendimiento de esta característica? 

El impacto en el rendimiento general de ejecución paso a paso depende de la aplicación. La sobrecarga de tomar una instantánea es aproximadamente de 30 ms. Cuando se toma una instantánea, se bifurca el proceso de la aplicación y se suspende la copia bifurcada. Cuando ve una instantánea, Visual Studio se conecta a la copia del proceso bifurcada. En cada instantánea, Visual Studio copia solo la tabla de páginas y establece páginas para la copia en escritura. Si cambian los objetos del montón entre los pasos del depurador con instantáneas asociadas, se copia la tabla de la página correspondiente, lo que resulta en un costo de memoria mínimo. Si Visual Studio detecta que no hay memoria suficiente para tomar una instantánea, no la toma.

## <a name="known-issues"></a>Problemas conocidos
* Si está utilizando el modo de eventos e instantáneas de IntelliTrace en las versiones de Windows anteriores a Windows 10 Fall Creators Update (RS3), y la plataforma de destino de depuración de la aplicación se establece en x86, IntelliTrace no toma instantáneas.

    Soluciones:
  * Si está en la Actualización de aniversario de Windows 10 (RS1) y por debajo de la versión 10.0.14393.2273, [instale KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720).
  * Si está en Windows 10 Creators Update (RS2) y por debajo de la versión 10.0.15063.1112, [instale KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
  * Instale o actualice a Windows 10 Fall Creators Update (RS3).
  * Alternativamente:
    1. Instale el componente de conjunto de herramientas de VC++ 2015.3 v140 para el escritorio (x86, x64) del Instalador de Visual Studio.
    2. Compile la aplicación de destino.
    3. En la línea de comandos, use la herramienta editbin para establecer la marca `Largeaddressaware` para el destino ejecutable. Por ejemplo, es posible que use este comando (después de actualizar la ruta de acceso): "C:\Archivos de programa (x86)\Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Ruta de acceso\a\la\aplicación\app.exe".
    4. Presione **F5** para iniciar la depuración. Ahora se tomarán instantáneas en los pasos y puntos de interrupción del depurador.

       > [!Note]
       > La marca `Largeaddressaware` se debe establecer cada vez que se vuelve a generar el archivo ejecutable con cambios.

* Cuando se toma una instantánea del proceso de la aplicación en una aplicación que utiliza un archivo asignado a memoria persistente, el proceso con la instantánea mantiene un bloqueo exclusivo en el archivo asignado a memoria (incluso después de que el proceso primario haya liberado el bloqueo). Otros procesos todavía pueden leer pero no escribir en el archivo asignado a la memoria.

  Solución:
  * Desactive todas las instantáneas finalizando la sesión de depuración.

* Al depurar una aplicación cuyo proceso tiene un gran número de regiones de memoria exclusiva, como una aplicación que carga un gran número de archivos DLL, el rendimiento de la ejecución paso a paso con instantáneas habilitadas puede verse afectado. Este problema se corregirá en una futura versión de Windows. Si experimenta este problema, póngase en contacto con nosotros en stepback@microsoft.com.

* Al guardar un archivo con **Depurar > IntelliTrace > Guardar sesión de IntelliTrace** en el modo de eventos e instantáneas, los datos adicionales capturados desde instantáneas no están disponibles en el archivo .itrace. En los eventos de punto de interrupción y paso, verá la misma información como si hubiera guardado el archivo en modo de solo eventos de IntelliTrace.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido a utilizar la característica step-back de IntelliTrace. Es posible que desee obtener más información sobre otras características de IntelliTrace.

> [!div class="nextstepaction"]
> [Características de IntelliTrace](../debugger/intellitrace-features.md)
