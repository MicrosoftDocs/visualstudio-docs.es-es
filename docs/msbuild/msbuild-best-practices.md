---
title: "Procedimientos recomendados de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "procedimientos recomendados, MSBuild"
  - "MSBuild, procedimientos recomendados"
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Procedimientos recomendados de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le recomendamos los siguientes procedimientos para escribir scripts de MSBuild:  
  
-   Los valores de propiedad predeterminados se controlan mejor mediante el uso del atributo `Condition` sin declarar una propiedad cuyo valor predeterminado se puede reemplazar en la línea de comandos.  Por ejemplo, use  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Evite los caracteres comodín cuando seleccione elementos.  En su lugar, especifique los archivos explícitamente.  Esto hace más fácil realizar un seguimiento de los errores que pueden producirse al agregar o eliminar archivos.  
  
## Vea también  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)