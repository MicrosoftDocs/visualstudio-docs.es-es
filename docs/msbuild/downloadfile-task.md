---
title: DownloadFile (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#DownloadFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- DownloadFile task [MSBuild]
- MSBuild, DownloadFile task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb7b67c4ad567587278c805485e0b8e65ca44e94
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832929"
---
# <a name="downloadfile-task"></a>DownloadFile (Tarea)
Descarga los archivos especificados mediante el Protocolo de transferencia de hipertexto (HTTP).

>[!NOTE]
>La tarea DownloadFile solo está disponible en MSBuild 15.8 y versiones posteriores.
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `DownloadFile` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`DestinationFileName`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Nombre que se va a usar para el archivo descargado.  De forma predeterminada, el nombre de archivo deriva de `SourceUrl` o el servidor remoto.|
|`DestinationFolder`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica la carpeta de destino en la que se va a descargar el archivo.  Si no existe ninguna, se crea una carpeta.|
|`DownloadedFile`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el archivo que se ha descargado.|
|`Retries`|Parámetro `Int32` opcional.<br /><br /> Especifica cuántas veces se intenta descargar, si se ha producido un error en todos los intentos anteriores. Se establece en cero de forma predeterminada.|  
|`RetryDelayMilliseconds`|Parámetro `Int32` opcional.<br /><br /> Especifica el retraso en milisegundos entre los reintentos necesarios. Tiene como valor predeterminado 5000.|  
|`SkipUnchangedFiles`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, omite la descarga de archivos sin modificar. Tiene como valor predeterminado `true`. La tarea `DownloadFile` considera que los archivos están sin modificar si tienen el mismo tamaño y la misma hora de última modificación según el servidor remoto. <br /><br />**Nota:**  No todos los servidores HTTP indican la fecha de última modificación de los archivos, lo que hace que el archivo se vuelva a descargar.|
|`SourceUrl`|Parámetro `String` requerido.<br /><br /> Especifica la dirección URL que se va a descargar.|
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente descarga un archivo y lo incluye en los elementos `Content` antes de compilar el proyecto.
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>  
      <MyUrl>https://raw.githubusercontent.com/Microsoft/msbuild/master/LICENSE</MyUrl>
    </PropertyGroup>  

    <Target Name="DownloadContentFiles" BeforeTargets="Build">
        <DownloadFile
            SourceUrl="$(MyUrl)"
            DestinationFolder="$(MSBuildProjectDirectory)">
        <Output TaskParameter="DownloadedFile" ItemName="Content" />
      </DownloadFile>
    </Target>

</Project>
```
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
