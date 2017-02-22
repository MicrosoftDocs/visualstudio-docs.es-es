---
title: "Instrucciones Stop en Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
helpviewer_keywords: 
  - "puntos de interrupción, Stop (instrucciones)"
  - "depurar [Visual Basic], instrucciones Stop frente a puntos de interrupción"
  - "depurar código administrado, instrucciones Stop frente a puntos de interrupción"
  - "End (instrucciones)"
  - "Stop (instrucciones), acerca de las instrucciones Stop"
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instrucciones Stop en Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La instrucción Stop de Visual Basic proporciona una alternativa de programación al establecimiento de un punto de interrupción.  Cuando el depurador encuentra una instrucción Stop, interrumpe la ejecución del programa \(entra en el modo de interrupción\).  Los programadores de C\# pueden lograr el mismo efecto utilizando una llamada a System.Diagnostics.Debugger.Break.  
  
 Para establecer o quitar una instrucción Stop se edita el código fuente.  No se pueden establecer ni borrar instrucciones Stop mediante comandos del depurador, como se hace con un punto de interrupción.  
  
 A diferencia de una instrucción End, la instrucción Stop no restablece variables ni regresa al modo de diseño.  Para continuar la ejecución de la aplicación, puede elegir Continuar en el menú Depurar.  
  
 Cuando se ejecuta una aplicación de Visual Basic fuera del depurador, una instrucción Stop iniciará el depurador si está habilitada la depuración Just\-In\-Time.  Si no está habilitada la depuración Just\-In\-Time, la instrucción Stop se comporta como si fuera una instrucción End y termina la ejecución.  No se produce ningún evento QueryUnload o Unload, de manera que es necesario quitar todas las instrucciones Stop de la versión de lanzamiento en la aplicación de Visual Basic.  Para obtener más información, vea [Depuración Just\-In\-Time](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Para no tener que quitar instrucciones Stop, puede utilizar la compilación condicional:  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Otra alternativa consiste en utilizar una instrucción Assert en lugar de la instrucción Stop.  Una instrucción Debug.Assert sólo interrumpe la ejecución si no se cumple una condición especificada, y se quita automáticamente cuando se compila una versión de lanzamiento.  Para obtener más información, vea [Aserciones en el código administrado](../debugger/assertions-in-managed-code.md).  Si desea una instrucción Assert que interrumpa siempre la ejecución en la versión de depuración, puede hacer lo siguiente:  
  
```  
Debug.Assert(false)  
```  
  
 Otra alternativa más consiste en utilizar el método Debug.Fail:  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Tipos de proyectos de C\#, F\# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)