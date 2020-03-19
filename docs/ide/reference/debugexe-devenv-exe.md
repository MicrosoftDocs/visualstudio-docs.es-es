---
title: -DebugExe (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeae28288936b6723b53e826142a4888ad0bc8b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570146"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Abre el archivo ejecutable especificado que se va a depurar.

## <a name="syntax"></a>Sintaxis

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumentos

- *ExecutableFile*

  Obligatorio. Nombre de archivo y ruta de acceso de un archivo `.exe`. Si el archivo `.exe` no se encuentra o no existe, no se mostrará ninguna advertencia o error y Visual Studio se iniciará con normalidad.

## <a name="remarks"></a>Observaciones

Las cadenas que siguen al parámetro *ExecutableFile* se pasan a dicho archivo como argumentos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se abre el archivo `MyApplication.exe` para depurar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
