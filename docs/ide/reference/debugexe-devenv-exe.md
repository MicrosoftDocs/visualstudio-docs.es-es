---
title: -DebugExe (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07dfcbb6064d0f1043c0621534b953a5f5c63e82
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Abre el archivo ejecutable especificado que se va a depurar.

## <a name="syntax"></a>Sintaxis

```cmd
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Argumentos
 `ExecutableFile`

 Obligatorio. La ruta de acceso y el nombre de un archivo .exe.

 Si el archivo .exe no se encuentra o no existe, no se muestra ningún error ni advertencia y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicia normalmente.

## <a name="remarks"></a>Comentarios
 Las cadenas que siguen al parámetro `ExecutableFile` pasan a dicho archivo como argumentos.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, se abre el archivo `MyApplication.exe` para depurar.

```cmd
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)