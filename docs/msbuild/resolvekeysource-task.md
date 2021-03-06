---
title: Tarea ResolveKeySource | Microsoft Docs
description: Obtenga información sobre los parámetros de la tarea ResolveKeySource de MSBuild, que determina el origen de la clave de nombre seguro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveKeySource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveKeySource task [MSBuild]
- MSBuild, ResolveKeySource task
ms.assetid: 449f06c2-e9aa-4236-ab1e-c45c25452b2e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c06e012f84f1f18805ca458289c023679d0593d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912547"
---
# <a name="resolvekeysource-task"></a>ResolveKeySource (tarea)

Determina el origen de la clave de nombre seguro.

## <a name="task-parameters"></a>Parámetros de tareas

 En la siguiente tabla se describen los parámetros de la tarea `ResolveKeySource` .

|Parámetro|Descripción|
|---------------|-----------------|
|`AutoClosePasswordPromptShow`|Parámetro `Int32` opcional.<br /><br /> Obtiene o establece la cantidad de tiempo, en segundos, que se mostrará el mensaje de cuenta atrás.|
|`AutoClosePasswordPromptTimeout`|Parámetro `Int32` opcional.<br /><br /> Obtiene o establece la cantidad de tiempo, en segundos, que se esperará antes de cerrar el cuadro de diálogo de solicitud de contraseña.|
|`CertificateFile`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la ruta de acceso del archivo de certificado.|
|`CertificateThumbprint`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la huella digital del certificado.|
|`KeyFile`|Parámetro `String` opcional.<br /><br /> Obtiene o establece la ruta de acceso del archivo de claves.|
|`ResolvedKeyContainer`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece el contenedor de clave resuelta.|
|`ResolvedKeyFile`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece el archivo de clave resuelta.|
|`ResolvedThumbprint`|Parámetro de salida `String` opcional.<br /><br /> Obtiene o establece la huella digital resuelta del certificado.|
|`ShowImportDialogDespitePreviousFailures`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se muestra el cuadro de diálogo de importación a pesar de los errores anteriores.|
|`SuppressAutoClosePasswordPrompt`|Parámetro `Boolean` opcional.<br /><br /> Obtiene o establece un valor booleano que especifica si el cuadro de diálogo de contraseña no se debe cerrar automáticamente.|

## <a name="remarks"></a>Comentarios

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
