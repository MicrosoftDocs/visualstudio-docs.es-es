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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4eb1eb49cd6b29740fb6d365a98a51cc28387e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661677"
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

## <a name="remarks"></a>Comentarios

Las cadenas que siguen al parámetro *ExecutableFile* se pasan a dicho archivo como argumentos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se abre el archivo `MyApplication.exe` para depurar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)