---
title: -Deploy (devenv.exe)
description: Obtenga información sobre cómo usar el modificador Deploy de la línea de comandos de devenv para implementar una solución después de una compilación o recompilación.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Deploy switch
- Deploy Devenv switch
- deploying applications [Visual Studio], after build
- /Deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23064842d89ffb1e7fb5e521afe80caea5ffae56
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040713"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)

Implementa una solución después de una compilación o recompilación. Solo se aplica a los proyectos de código administrado.

## <a name="syntax"></a>Sintaxis

```shell
devenv SolutionName /Deploy [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Necesario. Ruta de acceso completa y nombre del archivo de solución.

- *SolnConfigName*

  Opcional. Nombre de la configuración de solución (por ejemplo, `Debug` o `Release`) que se usará para compilar la solución indicada en *SolutionName*. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`). Si no se especifica este argumento o se usa una cadena vacía (`""`), la herramienta usará la configuración activa de la solución.

- `/Project` *ProjName*

  Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede escribir el nombre para mostrar del proyecto o una ruta de acceso relativa desde la carpeta *SolutionName* al archivo del proyecto. También puede especificar el nombre y la ruta de acceso completa del archivo del proyecto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nombre de una configuración de compilación del proyecto (por ejemplo, `Debug` o `Release`) que se usará al compilar el proyecto indicado en `/Project`. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`). Si se especifica este modificador, reemplaza al argumento *SolnConfigName*.

- `/Out` *OutputFilename*

  Opcional. Nombre de un archivo que quiera enviar al resultado de la herramienta. Si el archivo ya existe, la herramienta anexa el resultado al final del archivo.

## <a name="remarks"></a>Comentarios

El proyecto especificado debe ser un proyecto de implementación. Si el proyecto especificado no es un proyecto de implementación, se producirá un error cuando se pase el proyecto que se ha compilado para implementarse.

Escriba las cadenas que incluyen espacios entre comillas dobles.

Se puede mostrar información de resumen de las compilaciones, incluidos los errores, en la **ventana de comandos** o en cualquier archivo de registro especificado con el modificador [/Out](out-devenv-exe.md).

## <a name="example"></a>Ejemplo

En este ejemplo se implementa el proyecto `CSharpWinApp` con la configuración de compilación del proyecto `Release` en `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
