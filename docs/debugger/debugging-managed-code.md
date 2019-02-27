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
ms.openlocfilehash: 14dc53413f646718b85ec9ea43d968dc9f64a96f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719329"
---
# <a name="debugging-managed-code"></a>Depurar código administrado

En esta sección se tratan problemas y técnicas de depuración comunes para aplicaciones administradas, o aplicaciones escritas en lenguajes basados en Common Language Runtime, como Visual Basic, C# y C++. Las técnicas descritas a continuación son técnicas de alto nivel. [Primer vistazo al depurador](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>En esta sección

[Mensajes de diagnóstico en la ventana de salida](../debugger/diagnostic-messages-in-the-output-window.md) describe la <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace> clases, con lo que puede escribir mensajes en tiempo de ejecución para el **salida** ventana. Estas clases incluyen métodos de salida que permiten enviar información sin interrumpir la ejecución y muestran información que también interrumpe la ejecución si no se cumple una condición especificada.

[Aserciones en el código administrado](../debugger/assertions-in-managed-code.md) Describe aserciones en el código administrado, que prueban condiciones especificadas como argumentos a `Assert` métodos. Además, en este tema se proporciona un código de ejemplo, información sobre el uso de los métodos de clase <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>, consideraciones sobre las versiones de lanzamiento y depuración del código, efectos secundarios, argumentos de Assert, personalización del comportamiento de Assert y archivos de configuración.

[Instrucciones Stop en Visual Basic](../debugger/stop-statements-in-visual-basic.md) describe el `Stop` instrucción, que proporciona una alternativa a establecer un punto de interrupción. También se proporciona código de ejemplo, junto con comparaciones entre las instrucciones `Stop` y `End`, así como entre las instrucciones `Stop` y `Assert`.

[Tutorial: Depurar un formulario Windows](../debugger/walkthrough-debugging-a-windows-form.md) proporciona instrucciones paso a paso para crear un formulario de Windows y depurar dicho formulario. Un Windows Form, un componente estándar de una aplicación para Windows administrada, es una de las aplicaciones administradas más comunes. En este tutorial se utiliza Visual C# y Visual Basic, pero normalmente las técnicas para crear un formulario Windows Forms con C++ son similares.

[Depurar el método OnStart](../debugger/how-to-debug-the-onstart-method.md) proporciona ejemplos de código para que pueda depurar el `OnStart` método de un servicio administrado de Windows. Para depurar el método `OnStart` de un servicio de Windows, se deben agregar algunas líneas de código para simular el servicio.

[Depuración en modo mixto](../debugger/debugging-mixed-mode-applications.md) explica la depuración de aplicaciones en modo mixto. Esto significa cualquier aplicación que combine código nativo con código administrado.

[Error: No se puede depurar porque un depurador del kernel está habilitado en el sistema](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md) describe un mensaje de error que se produce si se intenta depurar código administrado en un [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], o del sistema de Windows NT que se inició en modo de depuración.

[La optimización JIT y depuración](../debugger/jit-optimization-and-debugging.md) se describen los efectos de la optimización JIT de depuración.

[Depurar LINQ y DLINQ](../debugger/debugging-linq.md) trata las técnicas para depurar consultas LINQ.

[Tutorial: Depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md) se describe cómo usar el **tareas paralelas** y **pilas paralelas** ventanas para depurar una aplicación paralela.

## <a name="related-sections"></a>Secciones relacionadas

[IntelliTrace](../debugger/intellitrace.md) encontrar errores más rápidos y fáciles grabando el historial de ejecución de la aplicación con IntelliTrace. Avanzar y retroceder por las llamadas y eventos registrados para examinar el estado de la aplicación en puntos en el tiempo clave. Depurar el código sin tener que establecer tantos puntos de interrupción o reiniciar la aplicación con tanta frecuencia. Requiere Visual Studio Enterprise.

[Seguimiento e instrumentación de aplicaciones](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications) describe la traza, una forma de supervisar la ejecución de la aplicación mientras se está ejecutando y la instrumentación, lo que implica colocar instrucciones de seguimiento en puntos estratégicos del código. En este tema también se proporcionan vínculos a una introducción a la instrumentación y la traza, modificadores de traza, agentes de escucha de traza, traza del código en una aplicación, adición de instrucciones de traza al código de una aplicación y compilación condicional con <xref:System.Diagnostics.Debug> y <xref:System.Diagnostics.Trace>.

[/ ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) describe una opción del vinculador que agrega <xref:System.Diagnostics.DebuggableAttribute> al código escrito con C++. Este atributo es necesario para utilizar características de depuración como la asociación con C++.

[Depurar aplicaciones de servicio de Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications) proporciona consideraciones para la depuración de aplicaciones de servicio de Windows, incluida la configuración de, asociar al proceso, depurar el código en el servicio `OnStart` método y el código en la ventana principal método, establecer puntos de interrupción y usar el Administrador de Control de servicios para iniciar, detengan, pausar y con el servicio.

[Depuración y generación de perfiles](/dotnet/framework/debug-trace-profile/index) describe la depuración de aplicaciones de .NET Framework y los requisitos de configuración.

[Depurar Script y aplicaciones Web](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications) describe comunes de depuración de problemas y técnicas que pueden producirse al depurar script y aplicaciones Web.

[Novedades del depurador de Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md) descripción de las nuevas características de depuración agregadas en esta versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Depurar la página principal](../debugger/debugger-feature-tour.md) proporciona vínculos a secciones más amplias de la documentación de depuración. Incluye: novedades del depurador, configuración y preparación, puntos de interrupción, control de excepciones, editar y continuar, depurar código administrado, depurar proyectos de Visual C++, depurar COM y ActiveX, depurar archivos DLL, depurar SQL y las referencias a la interfaz de usuario.

## <a name="see-also"></a>Vea también

[Tutorial: Depurar Windows personalizado Forms controles en tiempo de diseño](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[seguridad del depurador](../debugger/debugger-security.md)
[depuración en Visual Studio](../debugger/index.md) 
 [ Primer vistazo al depurador](../debugger/debugger-feature-tour.md)