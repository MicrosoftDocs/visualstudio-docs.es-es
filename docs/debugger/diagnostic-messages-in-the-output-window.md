---
title: "Enviar mensajes de diagnóstico a la ventana de salida | Documentos de Microsoft"
ms.custom: 
ms.date: 04/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: df071834a6ae36da0156c527284f6ffbfcee0e4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Enviar mensajes de diagnóstico a la ventana de salida
Puede escribir mensajes en tiempo de ejecución para la **salida** ventana mediante el `Debug` clase o la `Trace` (clase), que forman parte de la <xref:System.Diagnostics> biblioteca de clases. Utilice la clase Debug si sólo genera resultados en la versión de depuración del programa. Utilice la clase Trace si desea generar resultados en las versiones de depuración y de lanzamiento.  
  
## <a name="output-methods"></a>Métodos de salida  
 Las clases <xref:System.Diagnostics.Trace> y <xref:System.Diagnostics.Debug> proporcionan los siguientes métodos de salida:  
  
-   Diversos métodos `Write`, que envían información sin interrumpir la ejecución. Estos métodos reemplazan el método `Debug.Print` que se utilizaba en versiones anteriores de Visual Basic.  
  
-   Los métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, que interrumpen la ejecución y envían información si se produce un error en una condición especificada. De forma predeterminada, el método `Assert` muestra la información en un cuadro de diálogo. Para obtener más información, consulte [aserciones en el código administrado](../debugger/assertions-in-managed-code.md).  
  
-   Los métodos <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, que interrumpen siempre la ejecución y envían información. De forma predeterminada, el método `Fail` muestra la información en un cuadro de diálogo.  
  
 Además del programa fuera de la aplicación, el **salida** ventana puede mostrar la información sobre:  
  
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