---
title: Tarea GenerateTrustInfo | Microsoft Docs
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
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ccbe11cefa730264e523390a0844086d6fb03ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149583"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Genera la información de confianza de la aplicación a partir del manifiesto base y de los parámetros `TargetZone` y `ExcludedPermissions`.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `GenerateTrustInfo`.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`ApplicationDependencies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados dependientes.|  
|`BaseManifest`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el manifiesto base desde el cual se va a generar la confianza de la aplicación.|  
|`ExcludedPermissions`|Parámetro `String` opcional.<br /><br /> Especifica uno o varios valores de identidad de permiso separados por punto y coma que se excluirán del conjunto de permisos predeterminado de la zona.|  
|`TargetZone`|Parámetro `String` opcional.<br /><br /> Especifica un conjunto de permisos predeterminados de zona, que se obtiene a partir de la directiva de máquina.|  
|`TrustInfoFile`|Parámetro de salida obligatorio de tipo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica el archivo que contiene la información de confianza de seguridad de la aplicación.|  
  
## <a name="remarks"></a>Observaciones  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [clase base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
