---
title: Tarea GetFileHash | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFileHash task [MSBuild]
- MSBuild, GetFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab5da58b125f86627d54547bd9f6f7cddc16c4de
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622025"
---
# <a name="getfilehash-task"></a>Tarea GetFileHash

Calcula las sumas de comprobación del contenido de un archivo o conjunto de archivos.

Esta tarea se agregó en la versión 15.8, pero requiere una [solución alternativa](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) para usarla en versiones de MSBuild anteriores a la 16.0.

## <a name="task-parameters"></a>Parámetros de tareas

 En la siguiente tabla se describen los parámetros de la tarea `GetFileHash` .

|Parámetro|Descripción|
|---------------|-----------------|
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br />Archivos a los que se va a aplicar un algoritmo hash.|
|`Items`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br />Entrada `Files` con metadatos adicionales establecidos en el hash del archivo.|
|`Hash`|Parámetro de salida `String`.<br /><br />Hash del archivo. Esta salida solo se establece si se ha pasado exactamente un elemento.|
|`Algorithm`|Parámetro `String` opcional.<br /><br />Algoritmo. Valores permitidos: `SHA256`, `SHA384` y `SHA512`. Valor predeterminado: `SHA256`.|
|`MetadataName`|Parámetro `String` opcional.<br /><br />Nombre de metadatos donde se almacena el valor hash de cada elemento. Tiene como valor predeterminado `FileHash`.|
|`HashEncoding`|Parámetro `String` opcional.<br /><br />Codificación que se va a usar para generar los códigos hash. Tiene como valor predeterminado `hex`. Valores permitidos: `hex` y `base64`.|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa la tarea `GetFileHash` para determinar e imprimir la suma de comprobación de los elementos `FilesToHash`.

```xml
<Project>
  <ItemGroup>
    <FilesToHash Include="$(MSBuildThisFileDirectory)\*" />
  </ItemGroup>
  <Target Name="GetHash">
    <GetFileHash Files="@(FilesToHash)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)