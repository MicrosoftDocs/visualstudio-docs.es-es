---
title: "Mensajes de diagn&#243;stico en la ventana de resultados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.output"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debug (clase)"
  - "Debug.Print (reemplazos)"
  - "depurador, Resultados (ventana)"
  - "depurar [Visual Studio], mensajes de diagnóstico en la ventana de resultados"
  - "diagnóstico"
  - "mensajes de diagnóstico [C#]"
  - "diagnóstico"
  - "mensajes, diagnóstico"
  - "Resultados (ventana), mensajes de diagnóstico"
  - "System.Diagnostics.Debug (clase), Resultados (ventana)"
  - "System.Diagnostics.Trace (clase), Resultados (ventana)"
  - "Trace (clase), mensajes de diagnóstico"
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mensajes de diagn&#243;stico en la ventana de resultados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede escribir mensajes en tiempo de ejecución en la Ventana de salida mediante la clase Debug o la clase Trace, que forman parte de la biblioteca de clases <xref:System.Diagnostics>.  Utilice la clase Debug si sólo genera resultados en la versión de depuración del programa.  Utilice la clase Trace si desea generar resultados en las versiones de depuración y de lanzamiento.  
  
## Métodos de salida  
 Las clases <xref:System.Diagnostics.Trace> y <xref:System.Diagnostics.Debug> proporcionan los siguientes métodos de salida:  
  
-   Diversos métodos `Write`, que envían información sin interrumpir la ejecución.  Estos métodos reemplazan el método `Debug.Print` que se utilizaba en versiones anteriores de Visual Basic.  
  
-   Los métodos <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, que interrumpen la ejecución y envían información si se produce un error en una condición especificada.  De forma predeterminada, el método `Assert` muestra la información en un cuadro de diálogo.  Para obtener más información, vea [Aserciones en el código administrado](../debugger/assertions-in-managed-code.md).  
  
-   Los métodos <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> y <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, que interrumpen siempre la ejecución y envían información.  De forma predeterminada, el método `Fail` muestra la información en un cuadro de diálogo.  
  
 Además del programa fuera de la aplicación, la **Ventana de salida** puede mostrar información acerca de:  
  
-   Módulos que el depurador ha cargado o ha descargado.  
  
-   Excepciones que se producen.  
  
-   Procesos que salen.  
  
-   Subprocesos que salen.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Resultados \(Ventana\)](../ide/reference/output-window.md)   
 [Tracing and Instrumenting Applications](../Topic/Tracing%20and%20Instrumenting%20Applications.md)   
 [Introduction to Instrumentation and Tracing](http://msdn.microsoft.com/es-es/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Tipos de proyectos de C\#, F\# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)