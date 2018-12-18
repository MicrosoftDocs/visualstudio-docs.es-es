---
title: IntelliTrace | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.assetid: 486bfec2-39bd-4d78-892a-42352128ee52
caps.latest.revision: 142
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1cd1cc041970588cf7c90c2c6275100687e1bcb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737213"
---
# <a name="intellitrace"></a>IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IntelliTrace](https://docs.microsoft.com/visualstudio/debugger/intellitrace) .  
  
Puede emplear menos tiempo en la depuración de la aplicación si usa IntelliTrace para registrar y realizar un seguimiento del historial de ejecución del código. Los errores se detectan fácilmente ya que IntelliTrace le permite:  
  
- registrar eventos específicos;  
  
   Examinar el código relacionado, los datos que aparecen en la **variables locales** ventana durante los eventos del depurador y la información de llamadas de función  
  
- depurar errores que son difíciles de reproducir o que se producen en la implementación.  
  
  Puede usar IntelliTrace en Visual Studio Enterprise (pero no en las ediciones Professional o Community).  
  
## <a name="what-do-you-want-to-do"></a>¿Qué desea hacer?  
  
|||  
|-|-|  
|**Depurar la aplicación con IntelliTrace:**<br /><br /> -Mostrar eventos pasados.<br />-Mostrar mi información de llamadas con eventos anteriores.<br />-Guardar mi sesión de IntelliTrace.<br />-Controlar los datos que IntelliTrace recopila.|-   [Tutorial: Uso de IntelliTrace](../debugger/walkthrough-using-intellitrace.md)<br />     [Características de IntelliTrace](../debugger/intellitrace-features.md)<br />-   [Configurar IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)<br />-   [Depuración histórica](../debugger/historical-debugging.md)|  
|**Recopilar datos de IntelliTrace durante una sesión de prueba en Test Manager**|-   [Recopilar más datos de diagnóstico en pruebas manuales](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
|**Recopilar datos de IntelliTrace de las aplicaciones implementadas**|-   [Usar el recopilador independiente IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)|  
|**Iniciar la depuración desde un archivo de registro de IntelliTrace (archivo. iTrace).**|-   [Uso de los datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md)|  
  
##  <a name="IntelliTraceSupport"></a> ¿Qué aplicaciones puedo depurar con IntelliTrace?  
  
|||  
|-|-|  
|**Compatible**|-Aplicaciones Visual Basic y Visual C# que usan .NET Framework 2.0 o versiones posteriores.<br />     Puede depurar la mayoría de las aplicaciones, incluidas las aplicaciones de ASP.NET, Microsoft Azure, Windows Forms, WCF, WPF, Windows Workflow, SharePoint 2010, SharePoint 2013 y de 64 bits.<br />     Para depurar aplicaciones de SharePoint con IntelliTrace, consulte [Tutorial: depurar una aplicación de SharePoint mediante el uso de IntelliTrace](http://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4).<br />     Para depurar aplicaciones de Microsoft Azure con IntelliTrace, vea [depurar con IntelliTrace y Visual Studio un servicio de nube publicado](http://go.microsoft.com/fwlink/?LinkID=262248).|  
|**Compatibilidad limitada**|- F# aplicaciones en modo experimental<br />-Las aplicaciones de Windows Store compatibles solo para eventos|  
|**No se admite**|-C++, otros lenguajes y script<br />-Windows Services, Silverlight, Xbox o [!INCLUDE[winmobile](../includes/winmobile-md.md)] aplicaciones|  
  
> [!NOTE]
>  Si desea depurar un proceso que se está ejecutando, no puede usar IntelliTrace. Debe iniciar IntelliTrace cuando comience el proceso.  
  
##  <a name="IntelliTraceVSTraditional"></a> ¿Por qué depurar con IntelliTrace?  
 Tradicional o *live* depuración muestra solo la aplicación en su estado actual, con datos limitados sobre eventos pasados. Estos eventos deben inferirse basándose en el estado actual de la aplicación o hay que recrearlos ejecutando de nuevo la aplicación.  
  
 IntelliTrace amplía esta experiencia de depuración tradicional al registrar eventos y datos específicos en estos puntos en el tiempo. Esto le permite ver lo que ha sucedido en la aplicación sin reiniciarla, especialmente si se encuentra más allá de donde está el error. IntelliTrace está activado de forma predeterminada durante la depuración tradicional y recopila datos de forma automática e invisible. Esto permite cambiar fácilmente entre la depuración tradicional y la depuración de IntelliTrace para ver la información registrada. Consulte [las características de IntelliTrace](../debugger/intellitrace-features.md) y [¿qué datos recopila IntelliTrace?](#WhatData)  
  
 IntelliTrace también puede ayudar en la depuración de errores que son difíciles de reproducir o que se producen en la implementación. Puede recopilar datos de IntelliTrace y guardarlos en un archivo de registro de IntelliTrace (archivo .iTrace). Un archivo .iTrace contiene detalles sobre excepciones, eventos de rendimiento, solicitudes web, datos de prueba, subprocesos, módulos y otra información del sistema. Puede abrir este archivo en Visual Studio Enterprise, seleccionar un elemento e iniciar la depuración con IntelliTrace. De esta forma, podrá acceder a cualquier evento del archivo y ver detalles concretos sobre la aplicación en ese punto en el tiempo.  
  
 Puede guardar datos de IntelliTrace de estos orígenes:  
  
- Una sesión de IntelliTrace en Visual Studio 2015 Enterprise o versiones anteriores de Visual Studio Ultimate.  
  
- Sesiones de prueba en Microsoft Test Manager.  
  
- Aplicaciones web ASP.NET hospedadas en IIS, o aplicaciones de SharePoint 2010 y SharePoint 2013 que se ejecutan en la implementación cuando se usa Microsoft Monitoring Agent, solo o con System Center 2012. Consulte [mediante el recolector independiente IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) y [supervisión con Microsoft Monitoring Agent](http://technet.microsoft.com/library/dn465153.aspx).  
  
  A continuación se muestran algunos ejemplos de cómo IntelliTrace puede servir de ayuda en la depuración:  
  
- La aplicación ha dañado un archivo de datos, pero no se sabe dónde se produjo este evento.  
  
   Sin IntelliTrace, tiene que buscar en el código para encontrar todos los accesos posibles al archivo, colocar puntos de interrupción en esos accesos y volver a ejecutar la aplicación para encontrar el lugar donde se produjo el problema. Con IntelliTrace, puede ver todos los eventos de acceso a archivos recopilados y detalles concretos sobre la aplicación referentes al momento en que se produjo cada evento.  
  
- Se produce una excepción.  
  
   Sin IntelliTrace, aparece un mensaje sobre la excepción, pero no se proporciona mucha información sobre los eventos que produjeron la excepción. Puede examinar la pila de llamadas para ver la cadena de llamadas que produjeron la excepción, pero no puede ver la secuencia de eventos que se produjeron durante esas llamadas. Con IntelliTrace, puede examinar los eventos que se produjeron antes de la excepción.  
  
- La aplicación se bloquea en un equipo de prueba pero se ejecuta correctamente en un equipo de desarrollo.  
  
   Puede recopilar datos de IntelliTrace desde Microsoft Test Manager, guardar los datos en un archivo .iTrace y adjuntar este archivo a un elemento de trabajo de Team Foundation Server para analizarlo más adelante. Consulte [recopilar más datos de diagnóstico en pruebas manuales](http://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2) y [mediante datos de IntelliTrace guardado](../debugger/using-saved-intellitrace-data.md).  
  
- Se produce un error o un bloqueo en una aplicación implementada.  
  
   En aplicaciones basadas en Microsoft Azure, puede configurar la recopilación de datos de IntelliTrace antes de publicar la aplicación. Mientras se ejecuta la aplicación, IntelliTrace guarda los datos en un archivo .iTrace. Consulte [depurar un servicio en la nube publicado con IntelliTrace y Visual Studio](http://go.microsoft.com/fwlink/?LinkID=262248).  
  
   Para las aplicaciones web ASP.NET hospedadas en IIS 7.0, 7.5, y 8.0, y las aplicaciones de SharePoint 2010 o SharePoint 2013, utilice Microsoft Monitoring Agent, solo o con System Center 2012, para guardar los datos de IntelliTrace en un archivo .iTrace.  
  
   Esto es útil cuando desea diagnosticar problemas con aplicaciones en fase de implementación. Consulte [mediante el recolector independiente IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
##  <a name="WhatData"></a> ¿Qué datos recopila IntelliTrace?  
 **Recopilar información de eventos**  
  
 De forma predeterminada, IntelliTrace únicamente registra eventos de IntelliTrace: eventos del depurador, excepciones, eventos de .NET Framework y otros eventos del sistema que pueden ayudarle con la depuración. Puede elegir las clases de eventos de IntelliTrace que desee recopilar, salvo los eventos del depurador y las excepciones, que siempre se recopilan. Consulte [configurar IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
- **Eventos del depurador**  
  
   IntelliTrace registra siempre los eventos que se producen en el depurador de Visual Studio. Por ejemplo, iniciar la aplicación es un evento del depurador. Otros eventos del depurador son los eventos de parada, que hacen que la aplicación interrumpa la ejecución. Por ejemplo, el programa llega a un punto de interrupción, alcanza un punto de seguimiento o ejecuta un **paso** comando.  
  
   Para ayudar a mejorar el rendimiento, IntelliTrace no registra cada valor posible de un evento del depurador. En su lugar, registra estos valores:  
  
  -   Los valores en el **variables locales** ventana. Mantener la **variables locales** ventana abierta para ver estos valores.  
  
  -   Los valores en el **automático** solo si de ventana la **automático** ventana está abierta  
  
  -   Valores de información sobre datos que aparecen cuando mueve el puntero del mouse sobre una variable en la ventana de código fuente para ver su valor. IntelliTrace no recopila los valores de las informaciones sobre datos ancladas.  
  
- **Excepciones**  
  
   IntelliTrace registra el tipo y el mensaje de excepción de estas clases de excepciones:  
  
  -   Excepciones controladas en las que la excepción se inicia y se detecta  
  
  -   Excepciones no controladas  
  
- **Eventos de .NET framework**  
  
   De forma predeterminada, IntelliTrace registra los eventos más comunes de .NET Framework. Por ejemplo:  
  
  -   En el caso de un evento de acceso a archivo, IntelliTrace recopila el nombre de archivo.  
  
  -   Para un evento de activar casilla, IntelliTrace recopila el estado y el texto de la casilla.  
  
- **Eventos de aplicación de SharePoint 2010 y SharePoint 2013**  
  
   Puede registrar eventos de perfil de usuario y un subconjunto de eventos del sistema de registro unificado (ULS) para las aplicaciones de SharePoint 2010 y 2013 que se ejecutan fuera de Visual Studio. Puede guardar estos eventos en un archivo .iTrace. Requiere Visual Studio Enterprise 2015, una versión anterior de Visual Studio Ultimate, o [Microsoft Monitoring Agent](http://go.microsoft.com/fwlink/?LinkId=320384) que se ejecutan en **seguimiento** modo.  
  
   Al abrir el archivo .iTrace, especifique un identificador de correlación de SharePoint para buscar la solicitud web coincidente, ver los eventos registrados e iniciar la depuración desde un evento específico. Si el archivo contiene excepciones no controladas, puede elegir un identificador de correlación para empezar a depurar una excepción.  
  
   Vea:  
  
  -   [Usar el recopilador independiente de IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
  -   [Uso de datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md)  
  
  -   [Tutorial: Depurar una aplicación de SharePoint mediante IntelliTrace](http://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4)  
  
  **Recopilar información de llamadas de función**  
  
  Puede configurar IntelliTrace para recopilar información de llamadas de las funciones. Esta información permite ver un historial de la pila de llamadas y retroceder y avanzar por las llamadas en el código. Para cada llamada de función, IntelliTrace registra estos datos:  
  
- Nombre de la función  
  
- Valores de los tipos de datos primitivos pasados como parámetros en los puntos de entrada de la función y devueltos en los puntos de salida de la función  
  
- Valores de propiedades automáticas cuando estas se leen o se cambian  
  
- Punteros a objetos secundarios de primer nivel, pero no sus valores, salvo sin son null o no  
  
> [!NOTE]
>  IntelliTrace recopila solo los primeros 256 objetos en matrices y los primeros 256 caracteres de las cadenas.  
  
 Consulte [configurar IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 **Recopilar información de módulos**  
  
 Para controlar cuánta información de llamadas debe recopilar IntelliTrace, especifique solo los módulos que le interesan. Esto puede ayudar a mejorar el rendimiento de la aplicación durante la recopilación. Consulte [configurar IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
##  <a name="AffectPerformance"></a> ¿Ralentizará IntelliTrace la mi aplicación?  
 De forma predeterminada, IntelliTrace solamente recopila datos para los eventos de IntelliTrace seleccionados. Esto puede o no ralentizar la aplicación, dependiendo de la estructura y organización del código. Por ejemplo, si IntelliTrace registra un evento a menudo, la aplicación podría verse ralentizada. También podría hacer que usted se plantease refactorizar la aplicación.  
  
 La recopilación de la información de llamadas podría ralentizar considerablemente la aplicación. También podría aumentar el tamaño de los archivos de registro de IntelliTrace (archivos .iTrace) guardados en disco. Para reducir estos efectos, recopile la información de llamadas solo para los módulos que le interesen.  Para cambiar el tamaño máximo de los archivos. iTrace, vaya a **herramientas**, **opciones**, **IntelliTrace**, **avanzadas**. Consulte [configurar IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
## <a name="in-this-section"></a>En esta sección  
 [Características de IntelliTrace](../debugger/intellitrace-features.md)  
  
 [Configurar IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e)  
  
 [Incluir datos de seguimiento de diagnóstico con errores que son difíciles de reproducir](http://msdn.microsoft.com/library/944ae9af-5a55-4c58-b520-0108c03b3564)  
  
 [Diagnosis de problemas tras la implementación](../debugger/diagnose-problems-after-deployment.md)  
  
 [Uso de datos de IntelliTrace guardados](../debugger/using-saved-intellitrace-data.md)  
  
### <a name="blogs"></a>Blogs  
 [Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)  
  
### <a name="forums"></a>Foros  
 [Diagnósticos de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=262263)





