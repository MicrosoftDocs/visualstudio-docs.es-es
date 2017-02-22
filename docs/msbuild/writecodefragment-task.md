---
title: "WriteCodeFragment (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, WriteCodeFragment (tarea)"
  - "WriteCodeFragment (tarea) [MSBuild]"
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteCodeFragment (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Genera un archivo de código temporal del fragmento de código generado especificado.  No elimina el archivo.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `WriteCodeFragment`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AssemblyAttributes`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Descripción de los atributos que se van a escribir.  El valor del elemento `Include` es el nombre de tipo completo del atributo, por ejemplo, "System.AssemblyVersionAttribute".<br /><br /> Cada metadato es el par nombre\-valor de un parámetro, que debe ser del tipo `String`.  Algunos atributos solo permiten argumentos de constructor posicionales.  Sin embargo, puede utilizar estos argumentos en cualquier atributo.  Para definir los atributos de constructor posicionales, utilice nombres de metadatos que se asemejen a "\_Parameter1", "\_Parameter2" y así sucesivamente.<br /><br /> Un índice de parámetro no puede omitirse.|  
|`Language`|Parámetro `String` requerido.<br /><br /> Especifica el lenguaje del código que se desea generar.<br /><br /> `Language` puede ser cualquier lenguaje para el que un proveedor CodeDom esté disponible, por ejemplo, "C\#" o "Visual Basic".  El archivo emitido tendrá la extensión de nombre de archivo predeterminada de ese lenguaje.|  
|`OutputDirectory`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la carpeta de destino del código generado; normalmente es la carpeta intermedia.|  
|`OutputFile`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la ruta de acceso del archivo generado.  Si este parámetro se establece mediante un nombre de archivo, la carpeta de destino se antepone al nombre de archivo.  Si se establece utilizando una raíz, se omite la carpeta de destino.<br /><br /> Si no se establece este parámetro, el nombre del archivo de salida es la carpeta de destino, un nombre de archivo arbitrario y la extensión de nombre de archivo predeterminada del lenguaje especificado.|  
  
## Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)