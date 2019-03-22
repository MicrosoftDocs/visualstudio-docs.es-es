---
title: Depurar código administrado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 384b5dca1da11a430036cce2536e6859f3e98f94
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57868096"
---
# <a name="debugging-managed-code"></a>Depurar código administrado

En esta sección se tratan problemas y técnicas de depuración comunes para aplicaciones administradas, o aplicaciones escritas en lenguajes basados en Common Language Runtime, como Visual Basic, C# y C++. Las técnicas descritas a continuación son técnicas de alto nivel. [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>En esta sección

[Mensajes de diagnóstico en la ventana de resultados](../debugger/diagnostic-messages-in-the-output-window.md)\
Describe las clases <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>, con las que es posible escribir mensajes en tiempo de ejecución en la ventana de **salida**. Estas clases incluyen métodos de salida que permiten enviar información sin interrumpir la ejecución y muestran información que también interrumpe la ejecución si no se cumple una condición especificada.

[Aserciones en el código administrado](../debugger/assertions-in-managed-code.md)\
Describe aserciones en el código administrado, que prueban condiciones especificadas como argumentos para los métodos `Assert`. Además, en este tema se proporciona un código de ejemplo, información sobre el uso de los métodos de clase <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>, consideraciones sobre las versiones de lanzamiento y depuración del código, efectos secundarios, argumentos de Assert, personalización del comportamiento de Assert y archivos de configuración.

[Instrucciones Stop en Visual Basic](../debugger/stop-statements-in-visual-basic.md)\
Describe la instrucción `Stop`, que proporciona una alternativa al establecimiento de un punto de interrupción. También se proporciona código de ejemplo, junto con comparaciones entre las instrucciones `Stop` y `End`, así como entre las instrucciones `Stop` y `Assert`.

[Tutorial: Depurar Windows Forms](../debugger/walkthrough-debugging-a-windows-form.md)\
Ofrece instrucciones paso a paso para crear un Windows Form y para depurar dicho formulario. Un Windows Form, un componente estándar de una aplicación para Windows administrada, es una de las aplicaciones administradas más comunes. En este tutorial se utiliza Visual C# y Visual Basic, pero normalmente las técnicas para crear un formulario Windows Forms con C++ son similares.

[Depuración en el método OnStart](../debugger/how-to-debug-the-onstart-method.md)\
Proporciona ejemplos de código que permiten depurar el método `OnStart` de un servicio de Windows administrado. Para depurar el método `OnStart` de un servicio de Windows, se deben agregar algunas líneas de código para simular el servicio.

[Depuración en modo mixto](../debugger/debugging-mixed-mode-applications.md)\
Analiza la depuración de aplicaciones en modo mixto. Esto significa cualquier aplicación que combine código nativo con código administrado.

[Error: No se puede depurar porque un depurador del kernel está habilitado en el sistema](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)\
Describe un mensaje de error que se genera si se intenta depurar código administrado en un sistema con [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)] o Windows NT iniciado en modo de depuración.

[Optimización y depuración JIT](../debugger/jit-optimization-and-debugging.md)\
Describe los efectos de la optimización de JIT en la depuración.

[Depuración de LINQ y DLINQ](../debugger/debugging-linq.md)\
Analiza las técnicas para depurar consultas LINQ.

[Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)\
Describe cómo se usan las ventanas de herramientas **Tareas paralelas** y **Pilas paralelas** para depurar una aplicación paralela.

## <a name="related-sections"></a>Secciones relacionadas

[IntelliTrace](../debugger/intellitrace.md)\
Buscar errores más rápido y fácil grabando el historial de ejecución de la aplicación con IntelliTrace. Avanzar y retroceder por las llamadas y eventos registrados para examinar el estado de la aplicación en puntos en el tiempo clave. Depurar el código sin tener que establecer tantos puntos de interrupción o reiniciar la aplicación con tanta frecuencia. Requiere Visual Studio Enterprise.

[Seguimiento e instrumentación de aplicaciones](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)\
Describe la traza, una forma de supervisar la ejecución de una aplicación en funcionamiento, y la instrumentación, que permite colocar instrucciones de seguimiento en puntos estratégicos del código. En este tema también se proporcionan vínculos a una introducción a la instrumentación y la traza, modificadores de traza, agentes de escucha de traza, traza del código en una aplicación, adición de instrucciones de traza al código de una aplicación y compilación condicional con <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)\
Describe una opción del vinculador que agrega <xref:System.Diagnostics.DebuggableAttribute> a código escrito con C++. Este atributo es necesario para utilizar características de depuración como la asociación con C++.

[Depuración de aplicaciones de servicios de Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)\
Proporciona consideraciones sobre la depuración de aplicaciones de servicios de Windows, como la configuración, la asociación al proceso, la depuración del código del método `OnStart` y el método Main del servicio, el establecimiento de puntos de interrupción y el uso del Administrador de control de servicios para iniciar, detener, pausar y continuar el servicio.

[Depuración y generación de perfiles](/dotnet/framework/debug-trace-profile/index)\
Explica la depuración de las aplicaciones de .NET Framework y los requisitos de configuración.

[Depuración de scripts y aplicaciones web](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)\
Describe problemas y técnicas de depuración comunes que pueden aparecer en la depuración de scripts y aplicaciones Web.

[Depuración de la página principal](../debugger/debugger-feature-tour.md)\
Proporciona vínculos a secciones más amplias de la documentación relativa a la depuración. Incluye: novedades del depurador, configuración y preparación, puntos de interrupción, control de excepciones, editar y continuar, depurar código administrado, depurar proyectos de Visual C++, depurar COM y ActiveX, depurar archivos DLL, depurar SQL y las referencias a la interfaz de usuario.

## <a name="see-also"></a>Vea también

- [Tutorial: Depurar controles de formularios personalizados de Windows en tiempo de diseño](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
- [Seguridad del depurador](../debugger/debugger-security.md)
- [Depurar en Visual Studio](../debugger/index.md)
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)