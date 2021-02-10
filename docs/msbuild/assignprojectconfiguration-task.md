---
title: AssignProjectConfiguration (Tarea) | Microsoft Docs
description: Use la tarea AssignProjectConfiguration de MSBuild para aceptar una lista de cadenas de configuración y asignarlas a proyectos especificados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 18dab3d34f4c1c11fa2c212f12ca875cb1b7f3b8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964958"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration (Tarea)

Esta tarea acepta cadenas de configuración de lista y las asigna a los proyectos especificados.

## <a name="task-parameters"></a>Parámetros de tareas

 En la siguiente tabla se describen los parámetros de la tarea `AssignProjectConfiguration` .

|Parámetro|Description|
|---------------|-----------------|
|`ProjectReferences`|Parámetro de entrada <xref:Microsoft.Build.Framework.ITaskItem>`[]` necesario.<br /><br /> Proyectos que se van a configurar.|
|`SolutionConfigurationContents`|Parámetro de salida `string` opcional.<br /><br /> Contiene una cadena XML que incluye una configuración de proyecto para cada proyecto. Las configuraciones se asignan a los proyectos con nombre.|
|`DefaultToVcxPlatformMapping`|Parámetro de salida `string` opcional.<br /><br /> Contiene una lista delimitada por puntos y coma de asignaciones de los nombres de plataforma usados por la mayoría de los tipos a los usados por archivos *.vcxproj*.<br /><br /> Por ejemplo:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|
|`VcxToDefaultPlatformMapping`|Opcional<br /><br /> Parámetro de salida `string`.<br /><br /> Contiene una lista delimitada por puntos y coma de asignaciones de los nombres de plataforma de *.vcxproj* a los nombres de plataforma usados por la mayoría de los tipos.<br /><br /> Por ejemplo:<br /><br /> `"Win32=AnyCPU;X64=X64"`|
|`CurrentProjectConfiguration`|Parámetro de salida `string` opcional.<br /><br /> Contiene la configuración del proyecto actual.|
|`CurrentProjectPlatform`|Parámetro de salida `string` opcional.<br /><br /> Contiene la plataforma del proyecto actual.|
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Parámetro de salida `bool` opcional.<br /><br /> Contiene una marca que indica que se deben compilar las referencias incluso si se han deshabilitado en la configuración del proyecto.|
|`ShouldUnsetParentConfigurationAndPlatform`|Parámetro de salida `bool` opcional.<br /><br /> Contiene una marca que especifica si deben anular la configuración primaria y la plataforma.|
|`OutputType`|Parámetro de salida `string` opcional.<br /><br /> Contiene el tipo de salida del proyecto.|
|`ResolveConfigurationPlatformUsingMappings`|Parámetro de salida `bool` opcional.<br /><br /> Contiene una marca que indica si la compilación debe utilizar las asignaciones predeterminadas para resolver la configuración y la plataforma de las referencias del proyecto pasadas.|
|`AssignedProjects`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de rutas de acceso de referencia resueltas.|
|`UnassignedProjects`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de elementos de referencia de proyecto que no se pudieron resolver mediante la lista de resultados previamente resuelta.|

## <a name="remarks"></a>Comentarios

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
