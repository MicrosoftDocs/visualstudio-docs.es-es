---
title: "Depurar c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar aplicaciones web ASP.NET, código administrado"
  - "depurar código administrado"
  - "código administrado, depurar"
ms.assetid: fa3aff01-c271-4aa7-b5b1-def560471c84
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar c&#243;digo administrado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se tratan problemas y técnicas de depuración comunes para aplicaciones administradas, o aplicaciones escritas en lenguajes basados en Common Language Runtime, como Visual Basic, C\# y C\+\+.  Las técnicas descritas a continuación son técnicas de alto nivel.  Para obtener más información, vea [Usar el depurador](../debugger/debugger-basics.md).  
  
## En esta sección  
 [Mensajes de diagnóstico en la Ventana de salida](../debugger/diagnostic-messages-in-the-output-window.md)  
 Describe las clases <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>, con las que es posible escribir mensajes en tiempo de ejecución en la **Ventana de salida**.  Estas clases incluyen métodos de salida que permiten enviar información sin interrumpir la ejecución y muestran información que también interrumpe la ejecución si no se cumple una condición especificada.  
  
 [Aserciones en el código administrado](../debugger/assertions-in-managed-code.md)  
 Describe aserciones en el código administrado, que prueban condiciones especificadas como argumentos para los métodos `Assert`.  Además, en este tema se proporciona un código de ejemplo, información sobre el uso de los métodos de clase <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>, consideraciones sobre las versiones de lanzamiento y depuración del código, efectos secundarios, argumentos de Assert, personalización del comportamiento de Assert y archivos de configuración.  
  
 [Instrucciones Stop en Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
 Describe la instrucción `Stop`, que proporciona una alternativa al establecimiento de un punto de interrupción.  También se proporciona código de ejemplo, junto con comparaciones entre las instrucciones `Stop` y `End`, así como entre las instrucciones `Stop` y `Assert`.  
  
 [Tutorial: Depurar un Windows Form](../debugger/walkthrough-debugging-a-windows-form.md)  
 Ofrece instrucciones paso a paso para crear un Windows Form y para depurar dicho formulario.  Un Windows Form, un componente estándar de una aplicación para Windows administrada, es una de las aplicaciones administradas más comunes.  En este tutorial se utiliza Visual C\# y Visual Basic, pero normalmente las técnicas para crear un formulario Windows Forms con C\+\+ son similares.  
  
 [Depurar el método OnStart](../debugger/how-to-debug-the-onstart-method.md)  
 Proporciona ejemplos de código que permiten depurar el método `OnStart` de un servicio de Windows administrado.  Para depurar el método `OnStart` de un servicio de Windows, se deben agregar algunas líneas de código para simular el servicio.  
  
 [Depuración en modo mixto](../debugger/debugging-mixed-mode-applications.md)  
 Analiza la depuración de aplicaciones en modo mixto.  Esto significa cualquier aplicación que combine código nativo con código administrado.  
  
 [Error: No se puede depurar porque un depurador del kernel está habilitado en el sistema](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
 Describe un mensaje de error que se genera si se intenta depurar código administrado en un sistema con [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] o Windows NT iniciado en modo de depuración.  
  
 [Optimización y depuración JIT](../debugger/jit-optimization-and-debugging.md)  
 Describe los efectos de la optimización de JIT en la depuración.  
  
 [Depurar LINQ y DLINQ](../debugger/debugging-linq.md)  
 Analiza las técnicas para depurar consultas LINQ.  
  
 [Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Describe cómo se usan las ventanas de herramientas **Tareas paralelas** y **Pilas paralelas** para depurar una aplicación paralela.  
  
## Secciones relacionadas  
 [Uso de IntelliTrace](../debugger/intellitrace.md)  
 Buscar errores más rápido y fácil grabando el historial de ejecución de la aplicación con IntelliTrace.  Avanzar y retroceder por las llamadas y eventos registrados para examinar el estado de la aplicación en puntos en el tiempo clave.  Depurar el código sin tener que establecer tantos puntos de interrupción o reiniciar la aplicación con tanta frecuencia.  Requiere Visual Studio Ultimate.  
  
 [Traza e instrumentación de aplicaciones](../Topic/Tracing%20and%20Instrumenting%20Applications.md)  
 Describe la traza, una forma de supervisar la ejecución de una aplicación en funcionamiento, y la instrumentación, que permite colocar instrucciones de seguimiento en puntos estratégicos del código.  En este tema también se proporcionan vínculos a una introducción a la instrumentación y la traza, modificadores de traza, agentes de escucha de traza, traza del código en una aplicación, adición de instrucciones de traza al código de una aplicación y compilación condicional con <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>.  
  
 [\/ASSEMBLYDEBUG](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)  
 Describe una opción del vinculador que agrega <xref:System.Diagnostics.DebuggableAttribute> a código escrito con C\+\+.  Este atributo es necesario para utilizar características de depuración como la asociación con C\+\+.  
  
 [Depurar aplicaciones de servicios de Windows](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md)  
 Proporciona consideraciones sobre la depuración de aplicaciones de servicios de Windows, como la configuración, la asociación al proceso, la depuración del código del método `OnStart` y el método Main del servicio, el establecimiento de puntos de interrupción y el uso del Administrador de control de servicios para iniciar, detener, pausar y continuar el servicio.  
  
 [Depurar y generar perfiles](../Topic/Debugging,%20Tracing,%20and%20Profiling.md)  
 Explica la depuración de las aplicaciones de .NET Framework y los requisitos de configuración.  
  
 [Depurar scripts y aplicaciones Web](../debugger/debugging-web-applications-and-script.md)  
 Describe problemas y técnicas de depuración comunes que pueden aparecer en la depuración de scripts y aplicaciones Web.  
  
 [Lo nuevo para el depurador en Visual Studio 2015](../debugger/what’s-new-for-the-debugger-in-visual-studio-2015.md)  
 Describe las nuevas características de depuración agregadas en esta versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Depurar la página principal](../debugger/debugging-in-visual-studio.md)  
 Proporciona vínculos a secciones más amplias de la documentación relativa a la depuración.  Incluye: novedades del depurador, configuración y preparación, puntos de interrupción, control de excepciones, editar y continuar, depurar código administrado, depurar proyectos de Visual C\+\+, depurar COM y ActiveX, depurar archivos DLL, depurar SQL y las referencias a la interfaz de usuario.  
  
## Vea también  
 [Tutorial: Depurar controles personalizados de formularios Windows Forms en tiempo de diseño](../Topic/Walkthrough:%20Debugging%20Custom%20Windows%20Forms%20Controls%20at%20Design%20Time.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)