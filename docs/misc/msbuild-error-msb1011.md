---
title: "Error de MSBuild MSB1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.AmbiguousProjectError"
helpviewer_keywords: 
  - "MSB1011"
ms.assetid: f3cb16e5-288c-4dba-941f-a0ed3bf92db7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB1011
**Especifique el archivo de proyecto o de solución que se va a utilizar ya que esta carpeta contiene más de un archivo de proyecto o de solución.**  
  
 Si no se especifica un archivo de proyecto en la línea de comandos, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] busca en el directorio de trabajo actual un archivo con una extensión que termine en "proj" o "sln" y utiliza dicho archivo.  El directorio de trabajo actual contiene más de un archivo con una extensión que termina en "proj" o "sln".  
  
### Para corregir este error  
  
1.  Incluya el nombre del archivo de proyecto en la línea de comandos.  Por ejemplo, en lugar de escribir `msbuild`, escriba `msbuild myapp.proj`.  
  
## Vea también  
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)