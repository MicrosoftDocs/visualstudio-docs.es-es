---
title: "Ver una instantánea mediante IntelliTrace paso-back - Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c60d929-d993-49dc-9db3-43b30be9912b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 01e6203d7fbef7115ea2e380494735888995e343
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="view-snapshots-using-intellitrace-step-back-in-visual-studio"></a>Ver las instantáneas con devolución de paso de IntelliTrace en Visual Studio

Devolución de paso de IntelliTrace automáticamente toma una instantánea de la aplicación en cada punto de interrupción y el depurador evento de paso. Las instantáneas registradas le permiten volver a puntos de interrupción anteriores y ver el estado de la aplicación tal y como estaba en un momento anterior. La característica step-back de IntelliTrace puede permitirle ahorrar tiempo cuando desea ver el estado anterior de la aplicación, pero no desea reiniciar la depuración ni volver a crear el estado de aplicación que se desea.

Paso de copia de IntelliTrace está disponible a partir de Visual Studio Enterprise 2017 15.5 y versiones posteriores, y requiere actualización de aniversario de Windows 10 o superior. La característica se admite actualmente para la depuración de ASP.NET, formularios Windows Forms, WPF, aplicaciones de consola administrado y bibliotecas de clases administradas. No se admite actualmente la depuración de aplicaciones ASP.NET Core, .NET Core o UWP. 
  
## <a name="enable-intellitrace-events-and-snapshots-mode"></a>Habilitar el modo de eventos y las instantáneas de IntelliTrace 

1. En Visual Studio Enterprise, vaya a **Herramientas > Opciones > IntelliTrace** configuración y seleccione la opción **IntelliTrace eventos e instantáneas**. 

    ![Habilitar el modo de eventos de IntelliTrace e instantáneas](../debugger/media/intellitrace-enable-snapshots.png "modo de habilitar los eventos de IntelliTrace e instantáneas")

2. Abra el proyecto en Visual Studio.

3. Establezca uno o más puntos de interrupción en el proyecto e iniciar la depuración (presione **F5**), o iniciar la depuración recorriendo el código (**F10** o **F11**).

    IntelliTrace toma una instantánea del proceso de la aplicación en el depurador de cada evento de paso y de punto de interrupción. Estos eventos se registran en el **eventos** pestaña en el **herramientas de diagnóstico** ventana, junto con otros eventos de IntelliTrace. Para abrir esta ventana, elija **depurar** > **Windows** > **Mostrar herramientas de diagnóstico**.

    Un icono de la cámara aparece al lado de los eventos para el que las instantáneas están disponibles. 

    ![Ficha de eventos con instantáneas](../debugger/media/intellitrace-events-tab-with-snapshots.png "ficha de eventos con instantáneas en los puntos de interrupción y pasos")

    Por motivos de rendimiento, no se realizan las instantáneas que avance muy rápidamente. Si no aparece ningún icono de cámara aparece junto al paso, intente la ejecución paso a paso más lentamente.

## <a name="navigate-and-view-snapshots"></a>Navegar y ver las instantáneas

1. Navegar entre los eventos mediante el uso de la **paso atrás (Alt + [)** y **paso hacia delante (Alt +])** botones en la barra de herramientas de depuración.

    Estos botones navegar por los eventos que aparecen en la **eventos** pestaña en el **ventana de herramientas de diagnóstico**. Retroceder o avanzar paso a paso a un evento activa de manera automática la depuración histórica del evento seleccionado.

    ![Retroceder o avanzar botones](../debugger/media/intellitrace-step-back-icons-description.png "botones paso hacia atrás y hacia delante de paso")

    Al retroceder o avanzar paso a paso, Visual Studio entra en modo de depuración histórica. En este modo, el contexto del depurador cambia a la vez cuando se registró el evento seleccionado. Visual Studio también mueve el puntero a la línea de código en la ventana de código fuente correspondiente. 

    Desde esta vista, puede inspeccionar los valores de la **pila de llamadas**, **locales**, **automático**, y **inspección** windows. También puede desplazar el puntero sobre las variables para ver información sobre datos y realizar la evaluación de expresiones en el **inmediato** ventana. Los datos que se ven procede de la instantánea de tomadas en ese momento en el tiempo de proceso de la aplicación.

    Así, por ejemplo, si ha alcanzado un punto de interrupción y ha realizado un paso (**F10**), el **paso atrás** botón hace que Visual Studio en modo histórico en la línea de código correspondiente al punto de interrupción. 

    ![Modo histórico de activación en un evento con una instantánea](../debugger/media/intellitrace-historical-mode-with-snapshot.png "modo histórico de activación en un evento con una instantánea")

2. Para volver a la ejecución en directo, elija **continuar (F5)** o haga clic en el **volver a depuración en directo** vínculo en la barra de información. 

3. También puede ver una instantánea de la **eventos** ficha. Para ello, seleccione un evento con una instantánea y haga clic en **Activar depuración histórica**.

    También puede hacer clic en el icono de la cámara para activar depuración histórica.

    ![Activar depuración histórica en un evento](../debugger/media/intellitrace-activate-historical-debugging.png "Activar depuración histórica en un evento")

    A diferencia de la **Establecer instrucción siguiente** comando, ver una instantánea no vuelve a ejecutar el código; proporciona una vista estática del estado de la aplicación en un momento en el tiempo que se ha producido en el pasado.

    ![Información general de las copias de paso de IntelliTrace](../debugger/media/intellitrace-step-back-overview.png "información general de IntelliTrace paso invertido")

## <a name="next-steps"></a>Pasos siguientes  
 Para obtener información sobre cómo inspeccionar las variables en Visual Studio, vea [paseo por las características del depurador](../debugger/debugger-feature-tour.md)  
 Para obtener información general de depuración histórica, vea [depuración histórica](../debugger/historical-debugging.md).  

## <a name="frequently-asked-questions"></a>Preguntas más frecuentes

#### <a name="how-is-intellitrace-step-back-different-from-intellitrace-events-only-mode"></a>¿Cómo es diferente del modo de solo eventos de IntelliTrace devolución de paso de IntelliTrace?

IntelliTrace en modo de solo de eventos permiten activar depuración histórica en los puntos de interrupción y el depurador. Sin embargo, IntelliTrace captura solo los datos en el **locales** y **automático** windows si las ventanas abiertas, y captura solo los datos que se expanden y en la vista. En el modo solo eventos, a menudo no tiene una vista completa de las variables y los objetos complejos. Además, evaluación y ver datos de la expresión en el **inspección** ventana no es compatible. 

En el modo de eventos y las instantáneas, IntelliTrace captura la instantánea completa del proceso de la aplicación, incluidos objetos complejos. En una línea de código, puede ver la misma información como si se detiene en un punto de interrupción (y no es relevante si previamente se expande la información). Evaluación de expresiones también se admite cuando se ven una instantánea.  

#### <a name="what-is-the-performance-impact-of-this-feature"></a>¿Cuál es el impacto en el rendimiento de esta característica? 

El impacto en el rendimiento general de ejecución paso a paso depende de la aplicación. La sobrecarga de tomar una instantánea es aproximadamente 30 ms. Cuando se toma una instantánea, el proceso de la aplicación está bifurcado y se suspende la copia bifurcada. Cuando ve una instantánea, que Visual Studio se está asociando a la copia bifurcada del proceso. Para cada instantánea, Visual Studio copia la tabla de la página y establece las páginas para la copia en escritura. Si cambian los objetos del montón entre los pasos del depurador con las instantáneas asociadas, se copia, a continuación, la tabla de páginas respectivas resultante en el costo de memoria mínima. Si Visual Studio detecta que no hay memoria suficiente para tomar una instantánea, no tiene uno.
 
## <a name="known-issues"></a>Problemas conocidos  
* Si se usa el modo de eventos y las instantáneas de IntelliTrace en versiones de Windows anteriores a Windows 10 otoño creadores de actualización (RS3) y el destino de la plataforma de depuración de la aplicación se establece en x86, IntelliTrace no tomar instantáneas.

    Solución:
    * Instalar o actualizar a Windows 10 otoño creadores de actualización (RS3). 
    * O bien: 
        1. Instale el componente de conjunto de herramientas de VC++ 2015.3 v140 para el escritorio (x86, x64) del Instalador de Visual Studio.
        2. Compile la aplicación de destino.
        3. Desde la línea de comandos, utilice la herramienta editbin para establecer el `Largeaddressaware` marca para el archivo ejecutable de destino. Por ejemplo, podría usar este comando (después de actualizar la ruta de acceso): "C:\Program Files (x86) \Microsoft Visual Studio\Preview\Enterprise\VC\Tools\MSVC\14.12.25718\bin\Hostx86\x86\editbin.exe" /Largeaddressaware "C:\Path\To\Application\app.exe".
        4. Presione **F5** para iniciar la depuración. Ahora, las instantáneas se toman en los puntos de interrupción y el depurador.

        > [!Note]
        > El `Largeaddressaware` marca se debe establecer cada vez que se vuelve a generar el archivo ejecutable con los cambios.

* Cuando se toma una instantánea del proceso de la aplicación en una aplicación que utiliza un archivo asignado a memoria persistente, el proceso con la instantánea contiene un bloqueo exclusivo en el archivo asignado a memoria (incluso después de que el proceso primario haya liberado el bloqueo). Otros procesos están todavía puede leer, pero no escribir, en el archivo asignado a la memoria.

    Solución:
    * Desactive todas las instantáneas de finalizar la sesión de depuración. 

* Al guardar un archivo con **Depurar > IntelliTrace > sesión de IntelliTrace guardar** en el modo de eventos y las instantáneas, los datos adicionales que se capturan de instantáneas no están disponibles en el archivo. iTrace. En los eventos de punto de interrupción y examinar, verá la misma información como si se ha guardado el archivo en modo de solo eventos de IntelliTrace. 
