---
title: -Clean (devenv.exe)
description: Obtenga información sobre cómo usar el modificador Clean de la línea de comandos de devenv para limpiar todos los archivos intermedios y los directorios de salida.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4c3fdc30737a2266241e19ae40f840a41784cc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963294"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Limpia todos los archivos intermedios y directorios de salida.

## <a name="syntax"></a>Sintaxis

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Necesario. Ruta de acceso completa y nombre del archivo de solución.

- *Config* (Configuración).

  Opcional. Configuración (por ejemplo, `Debug` o `Release`) para borrar los archivos intermediarios de la solución indicada en *SolutionName*. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`). Si no se especifica este argumento o se usa una cadena vacía (`""`), la herramienta usará la configuración activa de la solución.

- `/Project` *ProjName*

  Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede escribir el nombre para mostrar del proyecto o una ruta de acceso relativa desde la carpeta *SolutionName* al archivo del proyecto. También puede especificar el nombre y la ruta de acceso completa del archivo del proyecto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nombre de la configuración de compilación de proyecto (como `Debug` o `Release`) que se usará al limpiar el proyecto indicado en `/Project`. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`). Si se especifica este modificador, reemplazará al argumento *Config*.

- `/Out` *OutputFilename*

  Opcional. Nombre de un archivo que quiera enviar al resultado de la herramienta. Si el archivo ya existe, la herramienta anexa el resultado al final del archivo.

## <a name="remarks"></a>Comentarios

Este modificador tiene la misma función que el comando de menú **Limpiar solución** en el IDE.

Escriba las cadenas que incluyen espacios entre comillas dobles.

Se puede mostrar información de resumen de las limpiezas y compilaciones, incluidos los errores, en la **ventana de comandos**, o bien en cualquier archivo de registro especificado con el modificador [/Out](out-devenv-exe.md).

Si no se especifica el modificador `/Project`, la acción de limpieza se realiza en todos los proyectos de la solución, incluso si se especifica *FileName* como un archivo del proyecto.

## <a name="example"></a>Ejemplo

En el primer ejemplo, se limpia la solución `MySolution`, mediante la configuración predeterminada especificada en el archivo de solución.

En el segundo ejemplo, se limpia el proyecto `CSharpWinApp` con la configuración de compilación del proyecto `Debug` en `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
