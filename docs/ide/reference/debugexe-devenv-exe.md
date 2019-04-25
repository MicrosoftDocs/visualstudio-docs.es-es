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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05266a6f1b5ee0be22e2edc8df1c03b720844f4f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924128"
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