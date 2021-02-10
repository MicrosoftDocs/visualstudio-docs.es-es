---
title: Clase base TaskExtension | Microsoft Docs
description: Obtenga información sobre los parámetros que la clase base Microsoft.Build.Tasks.TaskExtension agrega a las tareas que se heredan de ella.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6692cb16b3861d72bf713c22b2ecfb2ee95bc036
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965985"
---
# <a name="taskextension-base-class"></a>Clase base TaskExtension

Muchas tareas heredan de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Esta cadena de herencia agrega varios parámetros a las tareas que derivan de ellos. Estos parámetros se muestran en este documento.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de las clases base.

|Parámetro|Descripción|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica la interfaz del motor de compilación disponible para las tareas. El motor de compilación establece automáticamente este parámetro para permitir que las tareas vuelvan a llamarlo.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica la interfaz del motor de compilación disponible para las tareas. El motor de compilación establece automáticamente este parámetro para permitir que las tareas vuelvan a llamarlo.<br /><br /> Esta es una propiedad que permite que los autores de las tareas que heredan de esta clase no tengan que convertir el valor de `IBuildEngine` a `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica la interfaz del motor de compilación proporcionado por el host.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parámetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica la instancia del objeto host (puede ser null). El motor de compilación establece esta propiedad si el IDE del host tiene un objeto host asociado a esta tarea concreta.|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Parámetro de solo lectura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> opcional.<br /><br /> Obtiene un objeto `TaskLoggingHelperExtension` que contiene métodos de registro de tareas.|

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Tareas](../msbuild/msbuild-tasks.md)
