---
title: GetReferenceAssemblyPaths (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 485b8f9c19a8a91d686b603ee1be9da70b6c78e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987880"
---
# <a name="getreferenceassemblypaths-task"></a>GetReferenceAssemblyPaths (Tarea)
Devuelve las rutas de acceso al ensamblado de referencia de las diversas plataformas.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `GetReferenceAssemblyPaths` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ReferenceAssemblyPaths`|Parámetro de salida `String[]` opcional.<br /><br /> Devuelve la ruta, basándose en el parámetro `TargetFrameworkMoniker`. Si `TargetFrameworkMoniker` es NULL o está vacío, esta ruta será `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Parámetro de salida `String[]` opcional.<br /><br /> Devuelve la ruta, basándose en el parámetro `TargetFrameworkMoniker`, sin tener en cuenta la parte del perfil del moniker. Si `TargetFrameworkMoniker` es NULL o está vacío, esta ruta será `String.Empty`.|  
|`TargetFrameworkMoniker`|Parámetro `String` opcional.<br /><br /> Especifica el moniker de la versión de .NET Framework de destino que está asociado a las rutas de ensamblado de referencia.|  
|`RootPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso raíz que se va a usar para generar la ruta de ensamblado de referencia.|  
|`BypassFrameworkInstallChecks`|Parámetro <xref:System.Boolean> opcional.<br /><br /> Si `true`, omite las comprobaciones básicas que realiza `GetReferenceAssemblyPaths` de manera predeterminada para garantizar que determinados marcos de runtime estén instalados, dependiendo de la plataforma de destino.|  
|`TargetFrameworkMonikerDisplayName`|Parámetro de salida `String` opcional.<br /><br /> Especifica el nombre para mostrar del moniker de la versión de .NET Framework de destino.|  
  
## <a name="remarks"></a>Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)