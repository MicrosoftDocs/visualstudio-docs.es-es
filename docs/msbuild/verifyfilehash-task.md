---
title: Tarea VerifyFileHash | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9340657704900feb5ebdc188103109872ee39f5d
ms.sourcegitcommit: e3b9cbeea282f1b531c6a3f60515ebfe1688aa0e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/18/2020
ms.locfileid: "77439131"
---
# <a name="verifyfilehash-task"></a>Tarea VerifyFileHash

Comprueba que un archivo coincide con el hash de archivo esperado. Si el hash no coincide, se producirá un error en la tarea.

Esta tarea se agregó en la versión 15.8, pero requiere una [solución alternativa](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272) para usarla en versiones de MSBuild anteriores a la 16.0.

## <a name="task-parameters"></a>Parámetros de tareas

 En la siguiente tabla se describen los parámetros de la tarea `VerifyFileHash` .

|Parámetro|Descripción|
|---------------|-----------------|
|`File`|Parámetro `String` requerido.<br /><br />Archivo al que se va a aplicar el algoritmo hash y se va a validar.|
|`Hash`|Parámetro `String` requerido.<br /><br />Hash esperado del archivo.|
|`Algorithm`|Parámetro `String` opcional.<br /><br />Algoritmo. Valores permitidos: `SHA256`, `SHA384` y `SHA512`. Valor predeterminado: `SHA256`.|
|`HashEncoding`|Parámetro `String` opcional.<br /><br />Codificación que se va a usar para generar los códigos hash. Tiene como valor predeterminado `hex`. Valores permitidos: `hex` y `base64`.|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa la tarea `VerifyFileHash` para comprobar su propia suma de comprobación.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

En MSBuild 16.5 y versiones posteriores, si no quiere que la compilación genere errores cuando no coincida el hash (por ejemplo, al utilizar la comparación de hash como condición para el flujo de control), puede reducir la importancia del mensaje para que deje de mostrarse como advertencia con el código siguiente:

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
