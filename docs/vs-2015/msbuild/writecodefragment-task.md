---
title: Tarea WriteCodeFragment | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, WriteCodeFragment task
- WriteCodeFragment task [MSBuild]
ms.assetid: 1d2514b4-5bef-43bb-bebe-496da8ef063c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee0b819d0387ecbd0bec3a460bf3c63d3122b269
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796946"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Genera un archivo de código temporal a partir del fragmento de código generado especificado. No elimina el archivo.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `WriteCodeFragment` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AssemblyAttributes`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Descripción de los atributos que se van a escribir. El valor `Include` del elemento es el nombre de tipo completo del atributo, por ejemplo, "System.AssemblyVersionAttribute".<br /><br /> Cada fragmento de metadatos es el par nombre-valor de un parámetro, que debe ser de tipo `String`. Algunos atributos solo permiten argumentos de constructor posicional. Aun así, puede usar estos argumentos en cualquier atributo. Para establecer atributos de constructor posicional, use nombres de metadatos que sean similares a "_Parameter1", "_Parameter2", etc.<br /><br /> No se puede omitir un índice de parámetro.|  
|`Language`|Parámetro `String` requerido.<br /><br /> Especifica el lenguaje del código que se va a generar.<br /><br /> `Language` puede ser cualquier lenguaje para el que esté disponible un proveedor CodeDOM, por ejemplo, "C#" o "VisualBasic". El archivo emitido tendrá la extensión de nombre de archivo predeterminada para ese lenguaje.|  
|`OutputDirectory`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la carpeta de destino del código generado, normalmente la carpeta intermedia.|  
|`OutputFile`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la ruta de acceso del archivo que se ha generado. Si este parámetro se establece mediante el uso de un nombre de archivo, la carpeta de destino se antepone al nombre de archivo. Si se establece mediante el uso de una raíz, se omite la carpeta de destino.<br /><br /> Si no se establece este parámetro, el nombre del archivo de salida es la carpeta de destino, un nombre de archivo arbitrario y la extensión de nombre de archivo predeterminada para el lenguaje especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
