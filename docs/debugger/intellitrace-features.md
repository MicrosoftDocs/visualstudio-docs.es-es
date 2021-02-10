---
title: Características de IntelliTrace | Microsoft Docs
description: Obtenga información sobre las características de IntelliTrace en Visual Studio. Use IntelliTrace para registrar eventos y llamadas a métodos en la aplicación.
ms.custom: SEO-VS-2020
ms.date: 09/19/2018
ms.topic: conceptual
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4c974b9056b41de2e021f5918963d1d28ffa3db
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905005"
---
# <a name="intellitrace-features-c-visual-basic-c"></a>Características de IntelliTrace (C#, Visual Basic, C++)

IntelliTrace le permite registrar eventos y llamadas de método de su aplicación, por lo que puede examinar el estado de la misma (pila de llamadas y valores de variables locales) en distintos puntos de la ejecución. Empiece la depuración como de costumbre: IntelliTrace está activado de forma predeterminada y la información que registra se puede ver en la nueva ventana **Herramientas de diagnóstico** de la pestaña **Eventos**. Seleccione un evento y haga clic en **Activar depuración histórica** para ver la pila de llamadas y las variables locales registradas para este evento.

Para una descripción paso a paso, consulte [Tutorial: Uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md).

IntelliTrace está disponible en la edición Visual Studio Enterprise, pero no en las ediciones Professional o Community.

Para confirmar que IntelliTrace está activado, abra la página de opciones **Herramientas > Opciones > IntelliTrace**. **Habilitar IntelliTrace** debería estar activado de forma predeterminada.

> [!NOTE]
> Los valores de la página de opciones de **IntelliTrace** se aplican a Visual Studio en su totalidad, no a soluciones o proyectos individuales. Un cambio en estos valores se aplica a todas las instancias de Visual Studio, a todas las sesiones de depuración y a todos los proyectos o soluciones.

## <a name="choose-the-events-that-intellitrace-records-c-visual-basic"></a><a name="ChooseEvents"></a> Elección de los eventos que IntelliTrace registra (C#, Visual Basic)

Es posible activar o desactivar el registro de eventos específicos de IntelliTrace.

Si está depurando, detenga la depuración. Vaya a **Herramientas > Opciones > IntelliTrace > Eventos de IntelliTrace**. Elija los eventos que desea que IntelliTrace registre.

## <a name="collect-snapshots-c-visual-basic-c"></a><a name="Snapshots"></a> Recopilación de instantáneas (C#, Visual Basic, C++)

Esta característica no está habilitada de manera predeterminada, pero IntelliTrace puede capturar instantáneas de la aplicación en cada evento de paso del depurador y de punto de interrupción y esas instantáneas se pueden ver en una sesión de depuración histórica. Una instantánea le proporciona una vista del estado completo de la aplicación. Para habilitar la captura de instantáneas, vaya a **Herramientas > Opciones > IntelliTrace > General** y seleccione **Instantáneas de IntelliTrace (administradas y nativas)** . Para obtener más información, consulte [Inspeccionar el estado de aplicación anterior mediante step-back de IntelliTrace en Visual Studio](../debugger/view-historical-application-state.md).

Las instantáneas están disponibles en la versión 15.5 de Visual Studio Enterprise 2017 y versiones posteriores y requiere la Actualización de aniversario de Windows 10 o superior.  En el caso de las aplicaciones de .NET Core y ASP.NET Core, se requiere la versión 15.7 de Visual Studio Enterprise 2017. En el caso de las aplicaciones nativas dirigidas a Windows, se requiere Visual Studio Enterprise 2017 versión 15.9 Preview 2.

## <a name="collect-intellitrace-events-and-call-information-c-visual-basic"></a><a name="GoingFurther"></a> Recopilación de información de llamadas y eventos de IntelliTrace (C#, Visual Basic)

Además de los eventos, IntelliTrace puede registrar las llamadas de método, aunque esta opción no está habilitada de forma predeterminada. Para habilitar la recopilación de llamadas de método, vaya a **Herramientas > Opciones > IntelliTrace > General** y seleccione **Información de llamadas y eventos de IntelliTrace (solo administrados)** .

La información de llamadas no está disponible actualmente para aplicaciones de .NET Core y ASP.NET Core.

Esto le permite ver el historial de la pila de llamadas y retroceder o avanzar a través de las llamadas de código. IntelliTrace registra datos como nombres de método, puntos de entrada y salida de métodos, y ciertos valores de parámetros y valores devueltos.

> [!TIP]
> Esta opción no está habilitada de forma predeterminada porque agrega una sobrecarga considerable. IntelliTrace no solo tiene que interceptar todas las llamadas de método que realiza la aplicación, sino que también debe encargarse de un conjunto mucho mayor de datos a la hora de mostrarlos en pantalla o guardarlos en el disco.
>
> Para reducir la sobrecarga de rendimiento, restrinja la lista de eventos registrados por IntelliTrace y reduzca al mínimo el número de módulos que se recopilan. Para obtener más información, vea [Control de la cantidad de información de llamadas que registra IntelliTrace](../debugger/intellitrace-features.md#ControlCallData).

### <a name="use-the-navigation-gutter"></a>Uso del medianil de navegación

Puede usar el medianil de navegación que aparece a la izquierda de la ventana de código. Si no ve el medianil de navegación, vaya a **Herramientas > Opciones > IntelliTrace > Avanzado** y seleccione **Mostrar el medianil de navegación en modo de depuración**.

El medianil de navegación permite desplazarse hacia delante y hacia atrás por las llamadas de métodos y los eventos en el modo de depuración histórica. Para obtener más información sobre la depuración histórica, vea [Depuración histórica](../debugger/historical-debugging.md). Tiene una serie de comandos:

|Comando|Descripción|
|-|-|
|**Establecer aquí el contexto del depurador**|Establece el contexto de depuración en el período de tiempo de la llamada donde aparece.<br /><br /> Este icono solo aparece en la pila de llamadas actual.|
|**Volver al sitio de llamada**|Devolver el puntero y el contexto de depuración al punto en que se llamó a la función actual.<br /><br /> Si está en modo de depuración en directo, este comando activa la depuración histórica. Si regresa a la interrupción de ejecución original, la depuración histórica se desactiva y la depuración en directo se activa.|
|**Ir a llamada o evento de IntelliTrace anterior**|Devolver el puntero y el contexto de depuración a la llamada o evento anterior.<br /><br /> Si está en modo de depuración en directo, este comando activa la depuración histórica.|
|**Entrar**|Depurar paso a paso por instrucciones la función seleccionada actualmente.<br /><br /> Este comando solo está disponible en el modo de depuración histórica.|
|**Ir a llamada o evento de IntelliTrace siguiente**|Mover el puntero y el contexto de depuración a la siguiente llamada o evento para los que existen datos de IntelliTrace.<br /><br /> Este comando solo está disponible en el modo de depuración histórica.|
|**Ir a modo real**|Volver al modo de depuración en directo.|

### <a name="search-for-a-line-or-method-in-intellitrace"></a>Buscar una línea o método en IntelliTrace

Los métodos solo se pueden examinar si se habilita la información sobre llamadas de método. En el historial de IntelliTrace se puede buscar una línea o un método específicos. Con la ejecución de la depuración detenida, haga clic con el botón derecho en el cuerpo de la función para ver el menú contextual y, a continuación, haga clic en **Buscar esta línea en IntelliTrace** o **Buscar este método en IntelliTrace**.

### <a name="control-how-much-call-information-intellitrace-records"></a><a name="ControlCallData"></a> Control de la cantidad de información de llamadas que registra IntelliTrace

De forma predeterminada, IntelliTrace registra información sobre todos los módulos usados por la solución. No obstante, IntelliTrace se puede configurar para que registre información de llamadas solo para los módulos que le interesen. En **Herramientas > Opciones > IntelliTrace > Módulos**, puede especificar los módulos que desee incluir o excluir de IntelliTrace. De este modo, IntelliTrace recopilará únicamente los eventos que se originaron en los módulos especificados y las llamadas de método que se produjeron en los módulos de interés.

Para agregar varios módulos, utilice el carácter comodín * al principio o al final de la cadena. En los nombres de módulo, use nombres de archivo y no nombres de ensamblado. No se aceptan rutas de acceso a archivos.

Intente reducir al máximo el número de módulos, ya que el rendimiento mejora al tener que recopilar menos datos. También se obtiene menos ruido en la interfaz de usuario porque se deben recorrer menos datos.

## <a name="save-intellitrace-data-to-file-c-visual-basic-c"></a><a name="SaveSession"></a> Guardado de datos de IntelliTrace en un archivo (C#, Visual Basic, C++)

Para guardar los datos recopilados por IntelliTrace, vaya a **Depurar > IntelliTrace > Guardar sesión de IntelliTrace** mientras se está depurando y la aplicación está en estado de interrupción. El elemento de menú está deshabilitado y no podrá guardar los datos recopilados por IntelliTrace si la aplicación se está ejecutando o si se ha detenido la depuración.

IntelliTrace también se puede configurar para que guarde los datos automáticamente en un archivo; para ello, vaya a **Herramientas > Opciones > IntelliTrace > Avanzado** y seleccione **Almacenar registros de IntelliTrace en este directorio**. También puede configurar un tamaño fijo para el archivo generado; esto hará que IntelliTrace sobrescriba los datos más antiguos cuando se quede sin espacio. Visual Studio crea dos archivos para cada sesión de IntelliTrace cuando se guardan automáticamente y se activa el proceso de hospedaje de Visual Studio (vshost.exe).

> [!TIP]
> Para ahorrar espacio en disco, desactive el guardado automático de archivos cuando ya no los necesite. Los archivos existentes no se eliminarán. Siempre hay la posibilidad de guardar en archivo desde el menú contextual.

Al guardar los datos de IntelliTrace en un archivo, se crea un archivo .itrace para cada proceso en el que recopile IntelliTrace. A continuación puede abrir el archivo .itrace en Visual Studio desde **Archivo > Abrir > Archivo** y seleccione el archivo .itrace en el cuadro de diálogo Abrir archivo. Para obtener más información, vea el tema sobre el [uso de datos guardados de IntelliTrace](../debugger/using-saved-intellitrace-data.md).

## <a name="blogs"></a>Blogs

[IntelliTrace en Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)

[Walkthrough of Live Debugging using IntelliTrace in Visual Studio 2015 (Text Editor)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor/) (Tutorial de depuración en directo con IntelliTrace en Visual Studio 2015 [editor de texto])

[Walkthrough of Live Debugging using IntelliTrace in Visual Studio 2015 (Social Club)](https://devblogs.microsoft.com/devops/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club/) (Tutorial de depuración en directo con IntelliTrace en Visual Studio 2015 [club social])

[IntelliTrace in Visual Studio Enterprise 2015 now supports attach!](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach/) (IntelliTrace en Visual Studio Enterprise 2015 ahora permite asociar)

[Collect data from a windows service using the IntelliTrace Standalone Collector](https://devblogs.microsoft.com/devops/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector/) (Recopilación de datos de un servicio de Windows con el recopilador independiente IntelliTrace)

[Editing the IntelliTrace collection plan](https://devblogs.microsoft.com/devops/editing-the-intellitrace-collection-plan) (Edición del plan de recolección de IntelliTrace)

[Custom TraceSource and debugging using IntelliTrace](https://devblogs.microsoft.com/devops/custom-tracesource-and-debugging-using-intellitrace/) (TraceSource personalizado y depuración con IntelliTrace)

[IntelliTrace Standalone Collector and Application Pools running under Active Directory accounts](https://devblogs.microsoft.com/devops/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts/) (Recopilador independiente IntelliTrace y grupos de aplicaciones que se ejecutan en cuentas de Active Directory)

## <a name="forums"></a>Foros

[Depurador de Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home)

## <a name="videos"></a>Vídeos

[IntelliTrace Experience](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience) (Experiencia de IntelliTrace)

[Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716) (Depuración histórica con IntelliTrace en Microsoft Visual Studio Ultimate 2015)
