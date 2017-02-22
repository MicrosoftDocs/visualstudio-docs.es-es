---
title: "Extensibilidad de .NET compilador Platform (&#171;Roslyn&#187;) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Extensibilidad de .NET compilador Platform (&#171;Roslyn&#187;)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La misión de núcleo de .NET Compiler Platform \(«Roslyn»\) es abriendo los compiladores de C\# y Visual Basic al permitir que herramientas y a los desarrolladores compartir en los compiladores con gran cantidad de información acerca de los programas. Herramientas de análisis de código mejoran la calidad del código y generadores de ayuda en la creación de aplicaciones de código. Como herramientas inteligentes, necesita acceden a cada vez más el código profundo conocimiento de que poseen compiladores sólo. En lugar de traductores opacos \(código fuente y código objeto\), los compiladores Roslyn ofrecen las API que puede usar para tareas relacionadas con el código de las herramientas y aplicaciones.  
  
 La mejor parte es que los compiladores Roslyn, sus API, ejemplos y tutoriales y las herramientas real creadas sobre estas API son código abierto totalmente en [github.com\/dotnet\/roslyn](https://github.com/dotnet/Roslyn). Vaya al sitio de OSS para obtener más información y empezar a trabajar con Roslyn. Encontrará vínculos para obtener la última C\# y las características VB que puede utilizar como un usuario final, así como vínculos a empezar a trabajar como un generador de herramienta aprovecha las APIs Roslyn.  
  
## Vea también  
 [Introducción a los analizadores de Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)