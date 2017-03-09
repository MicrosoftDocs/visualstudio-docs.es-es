---
title: "Mostrar tipos de datos personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "autoexp.dat (archivo)"
  - "tipos de datos personalizados"
  - "tipos de datos [C#], personalizados"
  - "depurador, expandir tipos de datos"
  - "código administrado, tipos de datos personalizados"
  - "archivo mcee_cs.dat"
  - "archivo mcee_mc.dat"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Mostrar tipos de datos personalizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se puede personalizar la manera en que Visual Studio muestra los tipos de datos en las ventanas de variables del depurador.  
  
## Atributos  
 En C\# y Visual Basic, se pueden agregar expansiones para los datos personalizados mediante <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 En código de [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], Visual Basic no admite el atributo DebuggerBrowsable.  Esta limitación se ha quitado en las versiones más recientes de .NET Framework.  
  
## Visualizadores  
 Se puede escribir un visualizador para mostrar cualquier tipo de datos administrados.  Para obtener más información, vea [Cómo: Escribir un visualizador](../debugger/how-to-write-a-visualizer.md).  
  
## Código nativo  
 En el caso de código nativo, se pueden agregar expansiones de tipo de datos personalizados al archivo autoexp.dat, ubicado en el directorio Archivos de programa\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger.  El propio archivo incluye las instrucciones sobre cómo escribir reglas `autoexp`.  
  
> [!CAUTION]
>  La estructura de este archivo y la sintaxis de las reglas autoexp quizá cambien de una versión de Visual Studio a la siguiente.  
  
 Las vistas de tipos nativos también se pueden personalizar escribiendo un complemento de evaluador de expresiones.  Para obtener más información, vea [EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/es-es/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## Vea también  
 [Utilizar el atributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Ventanas Inspección e Inspección rápida](../debugger/watch-and-quickwatch-windows.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)