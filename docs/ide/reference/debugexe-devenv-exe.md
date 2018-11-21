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
ms.openlocfilehash: 1badcaba6f6461f6a2c6b73580d8d12c50481c2b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948782"
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