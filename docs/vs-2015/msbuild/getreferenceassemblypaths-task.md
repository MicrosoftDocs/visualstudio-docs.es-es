---
title: GetReferenceAssemblyPaths (Tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4563e1c28c17a173c211f979d2ca46503a6d19a7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805135"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Devuelve las rutas de acceso al ensamblado de referencia de las diversas plataformas.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `GetReferenceAssemblyPaths` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parámetro de salida `String[]` opcional.<br /><br /> Devuelve la ruta, basándose en el parámetro `TargetFrameworkMoniker`. Si `TargetFrameworkMoniker` es NULL o está vacío, esta ruta será `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parámetro de salida `String[]` opcional.<br /><br /> Devuelve la ruta, basándose en el parámetro `TargetFrameworkMoniker`, sin tener en cuenta la parte del perfil del moniker. Si `TargetFrameworkMoniker` es NULL o está vacío, esta ruta será `String.Empty`.|  
|`TargetFrameworkMoniker`|Parámetro `String` opcional.<br /><br /> Especifica el moniker de la versión de .NET Framework de destino que está asociado a las rutas de ensamblado de referencia.|  
|`RootPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso raíz que se va a usar para generar la ruta de ensamblado de referencia.|  
|`BypassFrameworkInstallChecks`|Parámetro [Boolean] (<!-- TODO: review code entity reference <xref:assetId:///Boolean?qualifyHint=False&amp;autoUpgrade=True>  -->) opcional.<br /><br /> Si `true`, omite las comprobaciones básicas que realiza `GetReferenceAssemblyPaths` de manera predeterminada para garantizar que determinados marcos de runtime estén instalados, dependiendo de la plataforma de destino.|  
|`TargetFrameworkMonikerDisplayName`|Parámetro de salida `String` opcional.<br /><br /> Especifica el nombre para mostrar del moniker de la versión de .NET Framework de destino.|  
  
## <a name="remarks"></a>Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
