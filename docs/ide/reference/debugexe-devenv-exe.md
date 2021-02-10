---
title: -DebugExe (devenv.exe)
description: Obtenga información sobre cómo usar el modificador DebugExe de la línea de comandos de devenv para abrir un archivo ejecutable especificado que se va a depurar.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5cdf770446b78b1a1bb4b55d61f4c3e9f50c4035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894613"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Abre el archivo ejecutable especificado que se va a depurar.

## <a name="syntax"></a>Sintaxis

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Argumentos

- *ExecutableFile*

  Necesario. Nombre de archivo y ruta de acceso de un archivo `.exe`. Si el archivo `.exe` no se encuentra o no existe, no se mostrará ninguna advertencia o error y Visual Studio se iniciará con normalidad.

## <a name="remarks"></a>Comentarios

Las cadenas que siguen al parámetro *ExecutableFile* se pasan a dicho archivo como argumentos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente, se abre el archivo `MyApplication.exe` para depurar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
