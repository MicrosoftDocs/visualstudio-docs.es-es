---
title: "Introducci&#243;n a los analizadores de Roslyn | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Introducci&#243;n a los analizadores de Roslyn
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con analizadores de código en directo, basado en el proyecto en Visual Studio, los autores de API pueden enviar el análisis de código específico de dominio como parte de sus paquetes de NuGet.  Dado que estos analizadores alimentan la plataforma del compilador .NET \(denominada "Roslyn"\), pueden producir advertencias en el código a medida que escribe, incluso antes de que termine la línea \(no esperar a compilar el código para detectar problemas\).  Los analizadores también ofrecen una corrección automática de código mediante el símbolo del sistema de bombilla de Visual Studio para permitir que el código de limpieza inmediatamente  
  
## Introducción  
 [Los analizadores de código activo Roslyn introducción y tutorial](https://msdn.microsoft.com/en-us/magazine/dn879356.aspx)  
  
 [Agregar código corrige Tutorial: Proporcionar correcciones a los usuarios los problemas de Analyzer](https://msdn.microsoft.com/en-us/magazine/dn904670.aspx)  
  
 [Introducción y Tutorial de charla de analizador del mundo Real](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Analizador de Roslyn reales](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que también puede ver como un [hablar](http://channel9.msdn.com/events/Build/2015/3-725)  
  
 [Varios ejemplos en github, se agrupan en tres tipos de analizadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)  
  
 [Introducción y recorrido de algunos analizadores hablar](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)  
  
## Otros recursos  
 [Más documentos en el sitio de github OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)  
  
 [Reglas de FxCop implementadas con analizadores de Roslyn en github](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)