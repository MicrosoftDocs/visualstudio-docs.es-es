---
title: -ProjectConfig (devenv.exe)
description: Obtenga información sobre cómo usar el modificador ProjectConfig de la línea de comandos de devenv para especificar una configuración de compilación de proyecto que se aplicará al compilar, limpiar, recompilar o implementar el proyecto.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06c6f98e9d022a7b253fdd0ea25a60ff01a4d756
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040074"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Especifica una configuración de compilación de proyecto que se aplicará al compilar, limpiar, recompilar o implementar el proyecto especificado en el argumento `/Project`.

## <a name="syntax"></a>Sintaxis

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Necesario. Ruta de acceso completa y nombre del archivo de solución.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Necesario. [Compila](build-devenv-exe.md), [limpia](clean-devenv-exe.md), [implementa](deploy-devenv-exe.md) o [recompila](rebuild-devenv-exe.md) el proyecto.

- *SolnConfigName*

  Opcional. Nombre de la configuración de solución (por ejemplo, `Debug` o `Release`) que se aplicará en la solución indicada en *SolutionName*. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`). Si no se especifica este argumento o se usa una cadena vacía (`""`), la herramienta usará la configuración activa de la solución.

- `/Project` *ProjName*

  Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede escribir el nombre para mostrar del proyecto o una ruta de acceso relativa desde la carpeta *SolutionName* al archivo del proyecto. También puede especificar el nombre y la ruta de acceso completa del archivo del proyecto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nombre de la configuración de compilación del proyecto (por ejemplo, `Debug` o `Release`) que se aplicará en el proyecto indicado en `/Project`. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`).

- `/Out` *OutputFilename*

  Opcional. Nombre de un archivo que quiera enviar al resultado de la herramienta. Si el archivo ya existe, la herramienta anexa el resultado al final del archivo.

## <a name="remarks"></a>Comentarios

El modificador `/ProjectConfig` tiene que usarse con el modificador `/Project` como parte de un comando `/Build`, /`Clean`, `/Deploy` o `/Rebuild`.

Escriba las cadenas que incluyen espacios entre comillas dobles.

Se puede mostrar información de resumen de las compilaciones, incluidos los errores, en la ventana de comandos o en cualquier archivo de registro especificado con el modificador `/Out`.

## <a name="example"></a>Ejemplo

El comando siguiente compila el proyecto `CSharpWinApp` con la configuración de compilación del proyecto `Debug` en `MySolution`:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
