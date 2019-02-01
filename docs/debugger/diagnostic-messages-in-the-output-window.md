---
title: Enviar mensajes a la ventana de salida | Microsoft Docs
ms.date: 11/08/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d3d65d888b2de32bc19235bc34acb9ce2a1d535
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54969514"
---
# <a name="send-messages-to-the-output-window"></a>Enrutamiento de mensajes a la ventana Salida

Puede escribir mensajes en tiempo de ejecución para el **salida** ventana mediante la <xref:System.Diagnostics.Debug> clase o el <xref:System.Diagnostics.Trace> (clase), que forman parte de la <xref:System.Diagnostics> biblioteca de clases. Use la <xref:System.Diagnostics.Debug> clase si desea que solo salida el *depurar* versión del programa. Use la <xref:System.Diagnostics.Trace> clase si desea que la salida en ambos el *depurar* y *versión* versiones.  
  
## <a name="output-methods"></a>Métodos de salida  
 Las clases <xref:System.Diagnostics.Trace> y <xref:System.Diagnostics.Debug> proporcionan los siguientes métodos de salida:  
  
- Diversos métodos `Write`, que envían información sin interrumpir la ejecución. Estos métodos reemplazan el método `Debug.Print` que se utilizaba en versiones anteriores de Visual Basic.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> métodos, que interrumpen la ejecución y la salida de información si se produce un error en una condición especificada. De forma predeterminada, el método `Assert` muestra la información en un cuadro de diálogo. Para obtener más información, vea [Aserciones en el código administrado](../debugger/assertions-in-managed-code.md).  
  
- El <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> métodos, que interrumpen siempre la información de ejecución y de salida. De forma predeterminada, el método `Fail` muestra la información en un cuadro de diálogo.  
  
El **salida** ventana también puede mostrar información acerca de:  
  
- Módulos que el depurador ha cargado o ha descargado.  
  
- Excepciones que se producen.  
  
- Procesos que salen.  
  
- Subprocesos que salen.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Ventana Resultados](../ide/reference/output-window.md)   
 [Seguimiento e instrumentar aplicaciones](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)
