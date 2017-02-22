---
title: "CPPClean (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.cppclean"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "CPPClean (tarea) (MSBuild (Visual C++))"
  - "MSBuild (Visual C++), CPPClean (tarea)"
ms.assetid: b62a482e-8fb5-4999-b50b-6605a078e291
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# CPPClean (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Elimina los archivos temporales que MSBuild crea cuando se compila un proyecto de Visual C\+\+.  El proceso de eliminar los archivos de compilación se conoce como *limpiar*.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea **CPPClean** .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**DeletedFiles**|Parámetro de salida `ITaskItem[]` opcional.<br /><br /> Define una matriz de elementos de archivo de salida de MSBuild que las tareas pueden usar y emitir.|  
|**DoDelete**|Parámetro **Boolean** opcional.<br /><br /> Si es `true`, borre los archivos de compilación temporales.|  
|**FilePatternsToDeleteOnClean**|Parámetro `String` requerido.<br /><br /> Especifica una lista de extensiones de archivo delimitada por puntos y coma de archivos que se desea limpiar.|  
|**FilesExcludedFromClean**|Parámetro `String` opcional.<br /><br /> Especifica una lista de archivos delimitada por puntos y coma que no se desea limpiar.|  
|**FoldersToClean**|Parámetro `String` requerido.<br /><br /> Especifica una lista de directorios delimitada por puntos y coma que se desea limpiar.  Puede especificar una ruta de acceso completa o relativa, y la ruta de acceso puede contener el símbolo de carácter comodín \(**\***\).|  
  
## Comentarios  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)