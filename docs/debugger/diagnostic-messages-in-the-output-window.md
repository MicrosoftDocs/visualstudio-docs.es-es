---
title: Enviar mensajes de diagnóstico a la ventana de salida | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27cec31b775ba5f8d201c81cbd65f5b161353986
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252302"
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Enviar mensajes de diagnóstico a la ventana de salida
Puede escribir mensajes en tiempo de ejecución para el **salida** ventana mediante la <xref:System.Diagnostics.Debug> clase o el <xref:System.Diagnostics.Trace> (clase), que forman parte de la <xref:System.Diagnostics> biblioteca de clases. Use la <xref:System.Diagnostics.Debug> clase si sólo genera resultados en el *depurar* versión del programa. Use la <xref:System.Diagnostics.Trace> clase si desea que la salida en ambos el *depurar* y *versión* versiones.  
  
## <a name="output-methods"></a>Métodos de salida  
 Las clases <xref:System.Diagnostics.Trace> y <xref:System.Diagnostics.Debug> proporcionan los siguientes métodos de salida:  
  
-   Diversos métodos `Write`, que envían información sin interrumpir la ejecución. Estos métodos reemplazan el método `Debug.Print` que se utilizaba en versiones anteriores de Visual Basic.  
  
-   Los métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, que interrumpen la ejecución y envían información si se produce un error en una condición especificada. De forma predeterminada, el método `Assert` muestra la información en un cuadro de diálogo. Para obtener más información, consulte [aserciones en el código administrado](../debugger/assertions-in-managed-code.md).  
  
-   Los métodos <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, que interrumpen siempre la ejecución y envían información. De forma predeterminada, el método `Fail` muestra la información en un cuadro de diálogo.  
  
 Además del programa fuera de la aplicación, el **salida** ventana puede mostrar información acerca de:  
  
-   Módulos que el depurador ha cargado o ha descargado.  
  
-   Excepciones que se producen.  
  
-   Procesos que salen.  
  
-   Subprocesos que salen.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Ventana de salida](../ide/reference/output-window.md)   
 [Seguimiento e instrumentación de aplicaciones](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)
