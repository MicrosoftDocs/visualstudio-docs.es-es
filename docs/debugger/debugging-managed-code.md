---
title: Depurar código administrado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: c40d5b088dbf41e56fff1ad41b6ce4381f6602b3
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39179484"
---
# <a name="debugging-managed-code"></a>Depurar código administrado

En esta sección se tratan problemas y técnicas de depuración comunes para aplicaciones administradas, o aplicaciones escritas en lenguajes basados en Common Language Runtime, como Visual Basic, C# y C++. Las técnicas descritas a continuación son técnicas de alto nivel. Para obtener más información, consulte [con el depurador](../debugger/getting-started-with-the-debugger.md).

## <a name="in-this-section"></a>En esta sección

[Mensajes de diagnóstico en la ventana de resultados](../debugger/diagnostic-messages-in-the-output-window.md)  
Describe el <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace> clases, con lo que puede escribir mensajes en tiempo de ejecución para el **salida** ventana. Estas clases incluyen métodos de salida que permiten enviar información sin interrumpir la ejecución y muestran información que también interrumpe la ejecución si no se cumple una condición especificada.

[Aserciones en el código administrado](../debugger/assertions-in-managed-code.md)  
Describe aserciones en el código administrado, que prueban condiciones especificadas como argumentos para los métodos `Assert`. Además, en este tema se proporciona un código de ejemplo, información sobre el uso de los métodos de clase <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>, consideraciones sobre las versiones de lanzamiento y depuración del código, efectos secundarios, argumentos de Assert, personalización del comportamiento de Assert y archivos de configuración.

[Instrucciones Stop en Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
Describe la instrucción `Stop`, que proporciona una alternativa al establecimiento de un punto de interrupción. También se proporciona código de ejemplo, junto con comparaciones entre las instrucciones `Stop` y `End`, así como entre las instrucciones `Stop` y `Assert`.

[Tutorial: Depurar Windows Forms](../debugger/walkthrough-debugging-a-windows-form.md)  
Ofrece instrucciones paso a paso para crear un Windows Form y para depurar dicho formulario. Un Windows Form, un componente estándar de una aplicación para Windows administrada, es una de las aplicaciones administradas más comunes. En este tutorial se utiliza Visual C# y Visual Basic, pero normalmente las técnicas para crear un formulario Windows Forms con C++ son similares.

[Depurar el método OnStart](../debugger/how-to-debug-the-onstart-method.md)  
Proporciona ejemplos de código que permiten depurar el método `OnStart` de un servicio de Windows administrado. Para depurar el método `OnStart` de un servicio de Windows, se deben agregar algunas líneas de código para simular el servicio.

[Depuración en modo mixto](../debugger/debugging-mixed-mode-applications.md)  
Analiza la depuración de aplicaciones en modo mixto. Esto significa cualquier aplicación que combine código nativo con código administrado.

[Error: No se puede depurar porque un depurador del kernel está habilitado en el sistema](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
Describe un mensaje de error que se produce si se intenta depurar código administrado en un [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], o del sistema de Windows NT que se ha iniciado en modo de depuración.

[Optimización y depuración JIT](../debugger/jit-optimization-and-debugging.md)  
Describe los efectos de la optimización de JIT en la depuración.

[Depurar LINQ y DLINQ](../debugger/debugging-linq.md)  
Analiza las técnicas para depurar consultas LINQ.

[Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md)  
Describe cómo utilizar el **tareas paralelas** y **pilas paralelas** ventanas para depurar una aplicación paralela.

## <a name="related-sections"></a>Secciones relacionadas

[IntelliTrace](../debugger/intellitrace.md) encontrar errores más rápidos y fáciles grabando el historial de ejecución de la aplicación con IntelliTrace. Avanzar y retroceder por las llamadas y eventos registrados para examinar el estado de la aplicación en puntos en el tiempo clave. Depurar el código sin tener que establecer tantos puntos de interrupción o reiniciar la aplicación con tanta frecuencia. Requiere Visual Studio Enterprise.

[Seguimiento e instrumentación de aplicaciones](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
Describe la traza, una forma de supervisar la ejecución de una aplicación en funcionamiento, y la instrumentación, que permite colocar instrucciones de seguimiento en puntos estratégicos del código. En este tema también se proporcionan vínculos a una introducción a la instrumentación y la traza, modificadores de traza, agentes de escucha de traza, traza del código en una aplicación, adición de instrucciones de traza al código de una aplicación y compilación condicional con <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>.

[/ ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)  
Describe una opción del vinculador que agrega <xref:System.Diagnostics.DebuggableAttribute> al código escrito con C++. Este atributo es necesario para utilizar características de depuración como la asociación con C++.

[Depurar aplicaciones de servicio de Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)  
Proporciona consideraciones sobre la depuración de aplicaciones de servicios de Windows, como la configuración, la asociación al proceso, la depuración del código del método `OnStart` y el método Main del servicio, el establecimiento de puntos de interrupción y el uso del Administrador de control de servicios para iniciar, detener, pausar y continuar el servicio.

[Depuración y generación de perfiles](/dotnet/framework/debug-trace-profile/index)  
Explica la depuración de las aplicaciones de .NET Framework y los requisitos de configuración.

[Depurar Script y aplicaciones Web](../debugger/debugging-web-applications-and-script.md)  
Describe problemas y técnicas de depuración comunes que pueden aparecer en la depuración de scripts y aplicaciones Web.

[Novedades del depurador de Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md)  
Describe las nuevas características de depuración agregadas en esta versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Depurar la página principal](../debugger/debugger-feature-tour.md)  
Proporciona vínculos a secciones más amplias de la documentación relativa a la depuración. Incluye: novedades del depurador, configuración y preparación, puntos de interrupción, control de excepciones, editar y continuar, depurar código administrado, depurar proyectos de Visual C++, depurar COM y ActiveX, depurar archivos DLL, depurar SQL y las referencias a la interfaz de usuario.

## <a name="see-also"></a>Vea también

[Tutorial: Depurar Windows personalizado Forms controles en tiempo de diseño](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[seguridad del depurador](../debugger/debugger-security.md)
[depuración en Visual Studio](../debugger/index.md) 
 [ Guía de características del depurador](../debugger/debugger-feature-tour.md)