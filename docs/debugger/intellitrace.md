---
title: IntelliTrace | Microsoft Docs
ms.date: 09/19/2018
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.overview
helpviewer_keywords:
- debugger, recording execution history
- debugging, recording execution history
- IntelliTrace [Visual Studio ALM]
- IntelliTrace, debugging applications
- debugger, (See also IntelliTrace [Visual Studio ALM])
- debugging, (See also IntelliTrace [Visual Studio ALM])
- IntelliTrace, collecting data from Test Manager
- IntelliTrace
- Test Manager, debugging with IntelliTrace
- IntelliTrace, debugging after a crash
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f17be088d27e473af0c45a950541fe0f5b77085
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905692"
---
# <a name="intellitrace-for-visual-studio-enterprise-c-visual-basic-c"></a>IntelliTrace para Visual Studio Enterprise (C#, Visual Basic, C++)

Puede emplear menos tiempo en la depuración de la aplicación si usa IntelliTrace para registrar y realizar un seguimiento del historial de ejecución del código. Los errores se detectan fácilmente ya que IntelliTrace le permite:

- registrar eventos específicos;

- examinar el código relacionado, los datos que aparecen en la ventana **Variables locales** durante los eventos del depurador y la información de llamadas de función;

- depurar errores que son difíciles de reproducir o que se producen en la implementación.

Puede usar IntelliTrace en Visual Studio Enterprise (pero no en las ediciones Professional o Community).

## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?

|||
|-|-|
|**Depurar la aplicación con IntelliTrace:**<br /><br /> - Deseo ver los últimos eventos.<br />- Deseo ver la información de llamadas con eventos anteriores.<br />- Guardar mi sesión de IntelliTrace.<br />- Controlar los datos que IntelliTrace recopila.|- [Inspeccionar el estado anterior de aplicación con IntelliTrace](../debugger/view-historical-application-state.md)<br />- [Tutorial: Uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />- [Características de IntelliTrace](../debugger/intellitrace-features.md)<br />- [Depuración histórica](../debugger/historical-debugging.md)|
|**Recopilar datos de IntelliTrace durante una sesión de prueba en Test Manager**|- [Recopilar más datos de diagnóstico en las pruebas manuales](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|
|**Recopilar datos de IntelliTrace de aplicaciones implementadas**|- [Usar el recopilador independiente de IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|
|**Iniciar la depuración de un archivo de registro de IntelliTrace (archivo .iTrace).**|- [Uso de datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md)|

## <a name="IntelliTraceSupport"></a> ¿Qué aplicaciones se pueden depurar con IntelliTrace?

| | |
|---------------------| - |
| **Compatibilidad total con** | - Aplicaciones de Visual Basic y Visual C# que usan .NET Framework 2.0 o versiones posteriores.<br/>Puede depurar la mayoría de las aplicaciones, incluidas las aplicaciones de ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 y de 64 bits.<br/>Para depurar aplicaciones de SharePoint con IntelliTrace, consulte [Tutorial: Depurar una aplicación de SharePoint mediante IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md).<br/> Para depurar aplicaciones de Microsoft Azure con IntelliTrace, vea [depurar con IntelliTrace y Visual Studio un servicio de nube publicado](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md). |
| **Compatibilidad limitada** | - C++ aplicaciones destinadas a Windows admiten la visualización de instantáneas mediante step-back de IntelliTrace. Se admiten solo eventos de depurador y la excepción.<br />-.NET core y aplicaciones de ASP.NET Core admiten para ciertos sólo eventos (eventos de controlador de MVC, ADO.NET y HTTPClient) en la depuración local. No se admite el recopilador independiente para las aplicaciones .NET Core o ASP.NET Core.<br />- Aplicaciones de F# en modo experimental<br />-Las aplicaciones UWP compatibles solo para eventos |
| **No se admite** | -Otros lenguajes y script<br />-Aplicaciones móviles de Windows, Silverlight, Xbox o servicios de Windows |

> [!NOTE]
> Si desea depurar un proceso que ya se está ejecutando, puede recopilar eventos de IntelliTrace solo (ninguna información de llamadas). Puede adjuntar a un proceso de 32 bits o 64 bits en el equipo local únicamente. No se recopilan los eventos que se producen antes de asociar al proceso.

## <a name="IntelliTraceVSTraditional"></a> ¿Por qué realizar la depuración con IntelliTrace?

La depuración tradicional o en *directo* solo muestra el estado actual de la aplicación, con datos limitados sobre eventos pasados. Estos eventos deben inferirse basándose en el estado actual de la aplicación o hay que recrearlos ejecutando de nuevo la aplicación.

IntelliTrace amplía esta experiencia de depuración tradicional al registrar eventos y datos específicos en estos puntos en el tiempo. Esto le permite ver lo que ha sucedido en la aplicación sin reiniciarla, especialmente si se encuentra más allá de donde está el error. IntelliTrace está activado de forma predeterminada durante la depuración tradicional y recopila datos de forma automática e invisible. Esto permite cambiar fácilmente entre la depuración tradicional y la depuración de IntelliTrace para ver la información registrada. Consulte [las características de IntelliTrace](../debugger/intellitrace-features.md) y [¿qué datos recopila IntelliTrace?](#WhatData)

IntelliTrace también puede ayudar en la depuración de errores que son difíciles de reproducir o que se producen en la implementación. Puede recopilar datos de IntelliTrace y guardarlos en un archivo de registro de IntelliTrace (archivo .iTrace). Un archivo .iTrace contiene detalles sobre excepciones, eventos de rendimiento, solicitudes web, datos de prueba, subprocesos, módulos y otra información del sistema. Puede abrir este archivo en Visual Studio Enterprise, seleccionar un elemento e iniciar la depuración con IntelliTrace. De esta forma, podrá acceder a cualquier evento del archivo y ver detalles concretos sobre la aplicación en ese punto en el tiempo.

Puede guardar datos de IntelliTrace de estos orígenes:

- Una sesión de IntelliTrace en Visual Studio 2015 Enterprise o versiones posteriores o versiones anteriores de Visual Studio Ultimate.

- Sesiones de prueba en Microsoft Test Manager.

- Aplicaciones web ASP.NET hospedadas en IIS, o aplicaciones de SharePoint 2010 y SharePoint 2013 que se ejecutan en la implementación cuando se usa Microsoft Monitoring Agent, solo o con System Center 2012. Consulte [usar el recolector independiente IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) y [supervisión con Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).

A continuación se muestran algunos ejemplos de cómo IntelliTrace puede servir de ayuda en la depuración:

- La aplicación ha dañado un archivo de datos, pero no se sabe dónde se produjo este evento.

     Sin IntelliTrace, tiene que buscar en el código para encontrar todos los accesos posibles al archivo, colocar puntos de interrupción en esos accesos y volver a ejecutar la aplicación para encontrar el lugar donde se produjo el problema. Con IntelliTrace, puede ver todos los eventos de acceso a archivos recopilados y detalles concretos sobre la aplicación referentes al momento en que se produjo cada evento.

- Se produce una excepción.

     Sin IntelliTrace, aparece un mensaje sobre la excepción, pero no se proporciona mucha información sobre los eventos que produjeron la excepción. Puede examinar la pila de llamadas para ver la cadena de llamadas que produjeron la excepción, pero no puede ver la secuencia de eventos que se produjeron durante esas llamadas. Con IntelliTrace, puede examinar los eventos que se produjeron antes de la excepción.

- La aplicación se bloquea en un equipo de prueba pero se ejecuta correctamente en un equipo de desarrollo.

     Puede recopilar datos de IntelliTrace desde Microsoft Test Manager, guardar los datos en un archivo .iTrace y adjuntar este archivo a un elemento de trabajo de Team Foundation Server para analizarlo más adelante. Consulte [recopilar más datos de diagnóstico en pruebas manuales](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts) y [Use datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md).

- Se produce un error o un bloqueo en una aplicación implementada.

     En aplicaciones basadas en Microsoft Azure, puede configurar la recopilación de datos de IntelliTrace antes de publicar la aplicación. Mientras se ejecuta la aplicación, IntelliTrace guarda los datos en un archivo .iTrace. Consulte [depurar un servicio en la nube publicado con IntelliTrace y Visual Studio](../azure/vs-azure-tools-intellitrace-debug-published-cloud-services.md).

     Para las aplicaciones web ASP.NET hospedadas en IIS 7.0, 7.5, y 8.0, y las aplicaciones de SharePoint 2010 o SharePoint 2013, utilice Microsoft Monitoring Agent, solo o con System Center 2012, para guardar los datos de IntelliTrace en un archivo .iTrace.

     Esto es útil cuando desea diagnosticar problemas con aplicaciones en fase de implementación. Consulte [usar el recolector independiente IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

## <a name="WhatData"></a> ¿Qué datos recopila IntelliTrace?

**Recopilar información de eventos**

De forma predeterminada, IntelliTrace únicamente registra eventos de IntelliTrace: eventos del depurador, excepciones, eventos de .NET Framework y otros eventos del sistema que pueden ayudarle con la depuración. Puede elegir las clases de eventos de IntelliTrace que desee recopilar, salvo los eventos del depurador y las excepciones, que siempre se recopilan. Consulte [las características de IntelliTrace](../debugger/intellitrace-features.md).

- **Eventos del depurador**

     IntelliTrace registra siempre los eventos que se producen en el depurador de Visual Studio. Por ejemplo, iniciar la aplicación es un evento del depurador. Otros eventos del depurador son los eventos de parada, que hacen que la aplicación interrumpa la ejecución. Por ejemplo, el programa encuentra un punto de interrupción, alcanza un punto de seguimiento o se ejecuta un comando **Paso**.

     De forma predeterminada, para incrementar el rendimiento, IntelliTrace no registra todos los valores posibles para un evento del depurador. En su lugar, registra estos valores:

  - Valores de la ventana **Expresiones locales**. Mantenga abierta la ventana **Expresiones locales** para ver estos valores.

  - Valores de la ventana **Automático**, solo si la ventana **Automático** está abierta

  - Valores de información sobre datos que aparecen cuando mueve el puntero del mouse sobre una variable en la ventana de código fuente para ver su valor. IntelliTrace no recopila los valores de las informaciones sobre datos ancladas.

    Cuando se habilita el modo de eventos de IntelliTrace e instantáneas, IntelliTrace tardará una instantánea del proceso de la aplicación en cada depurador **punto de interrupción** y **paso** eventos. Esto registrará los valores de la **variables locales**, **automático**, y **inspección** windows, independientemente de si las ventanas están abiertas o no. También se van a recopilar los valores de las sugerencias de datos anclados.

- **Excepciones**

     IntelliTrace registra el tipo y el mensaje de excepción de estas clases de excepciones:

    - Excepciones controladas en las que la excepción se inicia y se detecta

    - Excepciones no controladas

- **Eventos de .NET Framework**

   De forma predeterminada, IntelliTrace registra los eventos más comunes de .NET Framework. Por ejemplo, para un <xref:System.Windows.Forms.CheckBox.CheckedChanged?displayProperty=nameWithType> eventos, IntelliTrace recopila el estado y el texto.

- **Eventos de aplicación de SharePoint 2010 y SharePoint 2013**

     Puede registrar eventos de perfil de usuario y un subconjunto de eventos del sistema de registro unificado (ULS) para las aplicaciones de SharePoint 2010 y 2013 que se ejecutan fuera de Visual Studio. Puede guardar estos eventos en un archivo .iTrace. Requiere Visual Studio Enterprise 2015 o versiones posteriores, una versión anterior de Visual Studio Ultimate, o [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) que se ejecutan en **seguimiento** modo.

     Al abrir el archivo .iTrace, especifique un identificador de correlación de SharePoint para buscar la solicitud web coincidente, ver los eventos registrados e iniciar la depuración desde un evento específico. Si el archivo contiene excepciones no controladas, puede elegir un identificador de correlación para empezar a depurar una excepción.

     Vea:

    - [Uso del recopilador independiente de IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)

    - [Uso de datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md)

    - [Tutorial: Depurar una aplicación de SharePoint mediante IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)

**Captura de instantáneas**

Puede configurar IntelliTrace para capturar instantáneas en cada punto de interrupción y evento de paso del depurador. IntelliTrace registra el estado de la aplicación completa en cada instantánea, que le permite ver variables complejas y para evaluar expresiones.

> [!NOTE]
> El [recolector independiente IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) no admite la captura de instantáneas.

Consulte [inspeccionar el estado anterior de aplicación con IntelliTrace](../debugger/view-historical-application-state.md).

**Recopilar información de llamadas de función**

Puede configurar IntelliTrace para recopilar información de llamadas de las funciones. Esta información permite ver un historial de la pila de llamadas y retroceder y avanzar por las llamadas en el código. Para cada llamada de función, IntelliTrace registra estos datos:

- Nombre de la función
- Valores de los tipos de datos primitivos pasados como parámetros en los puntos de entrada de la función y devueltos en los puntos de salida de la función
- Valores de propiedades automáticas cuando estas se leen o se cambian
- Punteros a objetos secundarios de primer nivel, pero no sus valores, salvo sin son null o no

> [!NOTE]
> IntelliTrace recopila solo los primeros 256 objetos en matrices y los primeros 256 caracteres de las cadenas.

Consulte [inspeccionar la aplicación con depuración histórica](../debugger/historical-debugging-inspect-app.md).

**Recopilar información de módulo**

Para controlar cuánta información de llamadas debe recopilar IntelliTrace, especifique solo los módulos que le interesan. Esto puede ayudar a mejorar el rendimiento de la aplicación durante la recopilación. Consulte la sección [controlar cuánta información que IntelliTrace recopila](../debugger/intellitrace-features.md#ControlCallData) en las características de IntelliTrace.

## <a name="AffectPerformance"></a> ¿Ralentizará IntelliTrace la aplicación?

De forma predeterminada, IntelliTrace solamente recopila datos para los eventos de IntelliTrace seleccionados. Esto puede o no ralentizar la aplicación, dependiendo de la estructura y organización del código. Por ejemplo, si IntelliTrace registra un evento a menudo, la aplicación podría verse ralentizada. También podría hacer que usted se plantease refactorizar la aplicación.

La recopilación de la información de llamadas podría ralentizar considerablemente la aplicación. También podría aumentar el tamaño de los archivos de registro de IntelliTrace (archivos .iTrace) que se guardan en el disco. Para reducir estos efectos, recopile la información de llamadas solo para los módulos que le interesen.  Para cambiar el tamaño máximo de los archivos .iTrace, vaya a **Herramientas**, **Opciones**, **IntelliTrace**, **Avanzadas**.

### <a name="blogs"></a>Blogs

[Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Foros

[Diagnósticos de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)
