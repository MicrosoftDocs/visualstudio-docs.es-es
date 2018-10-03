---
title: Ver el estado anterior de la aplicación con IntelliTrace
ms.description: Learn how to take snapshots, and view snapshots with IntelliTrace step-back
ms.custom: mvc
ms.date: 09/19/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85b34fd85e8449949bb1e96efc1dd79aacbc1bd9
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2018
ms.locfileid: "48243957"
---
# <a name="inspect-previous-app-states-using-intellitrace-step-back-in-visual-studio"></a>Inspeccionar el estado de aplicación anterior mediante step-back de IntelliTrace en Visual Studio

Step-back de IntelliTrace toma automáticamente una instantánea de la aplicación en cada punto de interrupción y el depurador de evento de paso. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

Step-back de IntelliTrace está disponible a partir de Visual Studio Enterprise 2017 versión 15.5 y versiones posterior, y requiere Windows 10 Anniversary Update o posterior. La característica se admite actualmente para la depuración de ASP.NET, WinForms, WPF, aplicaciones de consola administrada y bibliotecas de clases administradas. A partir de Visual Studio Enterprise 2017 versión 15.7, también se admite la característica de ASP.NET Core y .NET Core. A partir de Visual Studio 2017 Enterprise versión 15.9 Preview 2, la característica también se admite para aplicaciones nativas destinadas a Windows. No se admite actualmente la depuración de aplicaciones de UWP.

En este tutorial va a:

> [!div class="checklist"]
> * Activar eventos de Intellitrace e instantáneas
> * Navegar por los eventos mediante los comandos de paso atrás y paso hacia delante
> * Ver las instantáneas de eventos
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Habilitar el modo de eventos e instantáneas de IntelliTrace 

1. Abra el proyecto en Visual Studio Enterprise.

1. Abra **herramientas** > **opciones** > **IntelliTrace** y seleccione la opción **IntelliTrace eventos e instantáneas** . 

    A partir de Visual Studio 2017 Enterprise versión 15.9 Preview 2, esta opción es **instantáneas de IntelliTrace (administradas y nativas)**. 

    ![Habilitar el modo de eventos de IntelliTrace e instantáneas](../debugger/media/intellitrace-enable-snapshots.png "modo Habilitar eventos de IntelliTrace e instantáneas")

1. Elija si desea configurar las opciones para ver instantáneas en excepciones, **IntelliTrace** > **avanzadas** desde el **opciones** cuadro de diálogo.

    Estas opciones están disponibles a partir de Visual Studio Enterprise 2017 versión 15.7.

    ![Configurar el comportamiento de las instantáneas en excepciones](../debugger/media/intellitrace-enable-snapshots-on-exceptions.png)

    Al habilitar eventos e instantáneas, toma de instantáneas en excepciones está también habilitada de forma predeterminada. Puede deshabilitar las instantáneas en excepciones anulando la selección de **recopilar las instantáneas en los eventos de excepción**. Cuando esta característica está habilitada, se toman instantáneas para las excepciones no controladas. Para las excepciones administradas, se toman instantáneas solo si se produce la excepción y si no es un volver a producir una excepción iniciada anteriormente. Puede establecer un número máximo de instantáneas en excepciones, seleccione un valor de la lista desplegable. El valor máximo se aplica por cada vez que la aplicación entra en modo de interrupción (por ejemplo, cuando la aplicación alcanza un punto de interrupción).

    > [!NOTE]
    > Las instantáneas se toman solo para eventos de excepción que IntelliTrace registra. Para código administrado, puede especificar qué eventos registra IntelliTrace seleccionando **herramientas** > **opciones** > **eventos de IntelliTrace**.

1. En el proyecto, establezca uno o varios puntos de interrupción e iniciar la depuración (presione **F5**), o iniciar la depuración pasando por el código (**F10** o **F11**).

    IntelliTrace toma una instantánea del proceso de la aplicación en cada paso del depurador, eventos de punto de interrupción y evento de excepción no controlada. Estos eventos se registran en el **eventos** pestaña en el **herramientas de diagnóstico** ventana, junto con otros eventos de IntelliTrace. Para abrir esta ventana, elija **depurar** > **Windows** > **Mostrar herramientas de diagnóstico**.

    Aparece un icono de cámara junto a los eventos para el que las instantáneas están disponibles. 

    ![Pestaña eventos con instantáneas](../debugger/media/intellitrace-events-tab-with-snapshots.png "ficha de eventos con instantáneas en los puntos de interrupción y pasos")

    Por motivos de rendimiento, no se toman instantáneas paso a paso muy rápidamente. Si no aparece ningún icono de cámara junto el paso, intente ejecutar paso a más lentamente.

## <a name="navigate-and-view-snapshots"></a>Navegar y ver las instantáneas

1. Navegar entre los eventos mediante el uso de la **paso atrás (Alt + [)** y **avanzar paso a paso (Alt +])** botones en la barra de herramientas de depuración.

    Estos botones navegar por los eventos que aparecen en la **eventos** pestaña en el **ventana Herramientas de diagnóstico**. Ejecución paso a paso hacia atrás o hacia delante a un evento automáticamente activa [depuración histórica](../debugger/historical-debugging.md) en el evento seleccionado.

    ![Avanzar y retroceder botones](../debugger/media/intellitrace-step-back-icons-description.png "botones Retroceder paso a paso y avanzar paso a paso")

    Al retroceder o avanzar paso a paso, Visual Studio entra en modo de depuración histórica. En este modo, el contexto del depurador cambia a la hora cuando se registró el evento seleccionado. Visual Studio también mueve el puntero a la línea de código en la ventana de código fuente correspondiente. 

    Desde esta vista, puede inspeccionar los valores de la **pila de llamadas**, **variables locales**, **automático**, y **inspección** windows. También puede mantener el mouse sobre las variables para ver información sobre datos y realizar la evaluación de expresiones en el **inmediato** ventana. Los datos que ve están desde la instantánea del proceso de la aplicación usa en ese momento dado.

    Así, por ejemplo, si ha realizado un paso y alcanza un punto de interrupción (**F10**), el **Retroceder paso a paso** botón pone a Visual Studio en el modo histórica en la línea de código correspondiente al punto de interrupción. 

    ![Modo histórica de activación en un evento con una instantánea](../debugger/media/intellitrace-historical-mode-with-snapshot.png "modo histórica de activación en un evento con una instantánea")

2. Para volver a la ejecución en vivo, elija **continuar (F5)** o haga clic en el **volver a depuración en directo** vínculo en la barra de información. 

3. También puede ver una instantánea de la **eventos** ficha. Para ello, seleccione un evento con una instantánea y haga clic en **Activar depuración histórica**.

    ![Activar depuración histórica en un evento](../debugger/media/intellitrace-activate-historical-debugging.png "Activar depuración histórica en un evento")

    A diferencia de la **Establecer instrucción siguiente** comando, ver una instantánea no vuelve a ejecutar el código; le proporciona una vista estática del estado de la aplicación en un punto en el tiempo que se ha producido en el pasado.

    ![Información general de step-back de IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "información general de a Step-back de IntelliTrace")

    Para obtener más información acerca de cómo inspeccionar las variables en Visual Studio, vea [paseo por las características del depurador](../debugger/debugger-feature-tour.md)  

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>¿Cómo es diferente del modo solo de los eventos de IntelliTrace step-back de IntelliTrace?

IntelliTrace en modo de solo los eventos permiten activar depuración histórica en puntos de interrupción y pasos del depurador. Sin embargo, IntelliTrace captura solo los datos en el **variables locales** y **automático** windows si las ventanas abiertas y sólo captura los datos que se expanden y en la vista. En modo de solo los eventos, a menudo no tiene una visión completa de las variables y objetos complejos. Además, evaluación y visualización de datos de la expresión en el **inspección** ventana no es compatible. 

En el modo de eventos e instantáneas, IntelliTrace captura la instantánea completa del proceso de la aplicación, incluidos objetos complejos. En una línea de código, puede ver la misma información como si se han detenido en un punto de interrupción (y no importa si anteriormente se expande la información). También se admite la evaluación de expresión al ver una instantánea.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>¿Qué es el impacto de rendimiento de esta característica? 

El impacto en el rendimiento general de ejecución paso a paso depende de la aplicación. La sobrecarga de tomar una instantánea es aproximadamente 30 ms. Cuando se toma una instantánea, se divide el proceso de la aplicación y se suspende la copia bifurcada. Cuando ve una instantánea, Visual Studio consiste en conectar a la copia del proceso bifurcada. Para cada instantánea, Visual Studio copia solo en la tabla de páginas y establece las páginas para la copia en escritura. Si cambian los objetos del montón entre los pasos del depurador con las instantáneas asociadas, a continuación, se copia en la tabla de la página correspondiente, lo que resulta en el costo de memoria mínima. Si Visual Studio detecta que no hay memoria suficiente para tomar una instantánea, no tiene uno.
 
## <a name="known-issues"></a>Problemas conocidos  
* Si está utilizando el modo de eventos e instantáneas de IntelliTrace en las versiones de Windows anteriores a Windows 10 Fall Creators Update (RS3), y la plataforma de destino de depuración de la aplicación se establece en x86, IntelliTrace no toma instantáneas.

    Soluciones:
    * Si está en la actualización de aniversario de Windows 10 (RS1) y por debajo de la versión 10.0.14393.2273, [instalar KB4103720](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720). 
    * Si está en Windows 10 Creators Update (RS2) y por debajo de la versión 10.0.15063.1112, [instalar KB4103722](https://support.microsoft.com/help/4103722/windows-10-update-4103722).
    * Instalar o actualizar a Windows 10 Fall Creators Update (RS3). 
    * O bien: 
        1. Instale el componente de conjunto de herramientas de VC++ 2015.3 v140 para el escritorio (x86, x64) del Instalador de Visual Studio.
        2. Compile la aplicación de destino.
        3. Desde la línea de comandos, use la herramienta editbin para establecer el `Largeaddressaware` marca para el archivo ejecutable de destino. Por ejemplo, podría utilizar este comando (después de actualizar la ruta de acceso): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
        4. Presione **F5** para iniciar la depuración. Ahora, las instantáneas se toman los puntos de interrupción y pasos del depurador.

        > [!Note]
        > El `Largeaddressaware` marca se debe establecer cada vez que se vuelve a generar el archivo ejecutable con los cambios.

* Cuando se toma una instantánea del proceso de la aplicación en una aplicación que utiliza un archivo asignado a memoria persistente, el proceso con la instantánea mantiene un bloqueo exclusivo en el archivo asignado a memoria (incluso después de que el proceso primario ha liberado el bloqueo). Otros procesos están todavía puede leer pero no escribir en el archivo asignado a la memoria.

    Solución:
    * Desactive todas las instantáneas al finalizar la sesión de depuración. 

* Al depurar una aplicación cuyo proceso tiene un gran número de regiones de memoria exclusiva, como una aplicación que carga un gran número de archivos DLL, ejecución paso a paso el rendimiento con instantáneas habilitadas puede verse afectado. Este problema se corregirá en una versión futura de Windows. Si experimenta este problema, en contacto con nosotros en stepback@microsoft.com. 

* Al guardar un archivo con **Depurar > IntelliTrace > sesión de IntelliTrace guardar** en el modo de eventos e instantáneas, los datos adicionales capturados desde instantáneas no están disponibles en el archivo. iTrace. En los eventos de punto de interrupción y paso, verá la misma información como si se ha guardado el archivo en modo de solo los eventos de IntelliTrace. 

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, ha aprendido cómo utilizar step-back de IntelliTrace. Es posible que desee obtener más información sobre otras características de IntelliTrace.

> [!div class="nextstepaction"]
> [Características de IntelliTrace](../debugger/intellitrace-features.md)
