---
title: Tarea WriteCodeFragment | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea WriteCodeFragment para generar un archivo de código temporal a partir del fragmento de código generado especificado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1bdab6066ce93475a2f6bb193c67da87c4fcaddd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888087"
---
# <a name="writecodefragment-task"></a>WriteCodeFragment (tarea)

Genera un archivo de código temporal a partir del fragmento de código generado especificado. No elimina el archivo.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `WriteCodeFragment` .

|Parámetro|Description|
|---------------|-----------------|
|`AssemblyAttributes`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Descripción de los atributos que se van a escribir. El valor `Include` del elemento es el nombre de tipo completo del atributo, por ejemplo, "System.AssemblyVersionAttribute".<br /><br /> Cada fragmento de metadatos es el par nombre-valor de un parámetro, que debe ser de tipo `String`. Algunos atributos solo permiten argumentos de constructor posicional. Aun así, puede usar estos argumentos en cualquier atributo. Para establecer atributos de constructor posicional, use nombres de metadatos que sean similares a "_Parameter1", "_Parameter2", etc.<br /><br /> No se puede omitir un índice de parámetro.|
|`Language`|Parámetro `String` requerido.<br /><br /> Especifica el lenguaje del código que se va a generar.<br /><br /> `Language` puede ser cualquier lenguaje para el que esté disponible un proveedor CodeDOM, por ejemplo, "C#" o "VisualBasic". El archivo emitido tendrá la extensión de nombre de archivo predeterminada para ese lenguaje.|
|`OutputDirectory`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la carpeta de destino del código generado, normalmente la carpeta intermedia.|
|`OutputFile`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica la ruta de acceso del archivo que se ha generado. Si este parámetro se establece mediante el uso de un nombre de archivo, la carpeta de destino se antepone al nombre de archivo. Si se establece mediante el uso de una raíz, se omite la carpeta de destino.<br /><br /> Si no se establece este parámetro, el nombre del archivo de salida es la carpeta de destino, un nombre de archivo arbitrario y la extensión de nombre de archivo predeterminada para el lenguaje especificado.|

## <a name="remarks"></a>Comentarios

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
