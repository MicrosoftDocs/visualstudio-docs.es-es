---
title: GetReferenceAssemblyPaths (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6063ca7f69d5dd04c0675090eb6c6deb3075bdf5
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
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
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)