---
title: -Rebuild (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 208bc533578d116fe55ad336f4aaee72eec94c3f
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/14/2019
ms.locfileid: "54268581"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Limpia y, después, compila la configuración de solución especificada.

## <a name="syntax"></a>Sintaxis

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Obligatorio. Ruta de acceso completa y nombre del archivo de solución.

- *SolnConfigName*

  Opcional. Nombre de la configuración de solución que se usará (por ejemplo, `Debug` o `Release`) para recompilar la solución indicada en *SolutionName*. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`). Si no se especifica este argumento o se usa una cadena vacía (`""`), la herramienta usará la configuración activa de la solución.

- `/Project` *ProjName*

  Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede escribir el nombre para mostrar del proyecto o una ruta de acceso relativa desde la carpeta *SolutionName* al archivo del proyecto. También puede especificar el nombre y la ruta de acceso completa del archivo del proyecto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. Nombre de la configuración de compilación del proyecto (como `Debug` o `Release`) que se usará al recompilar el proyecto indicado en `/Project`. Si hay más de una plataforma de solución disponible, también tendrá que especificar la plataforma (por ejemplo, `Debug|Win32`). Si se especifica este modificador, reemplaza al argumento *SolnConfigName*.

- `/Out` *OutputFilename*

  Opcional. Nombre de un archivo que quiera enviar al resultado de la herramienta. Si el archivo ya existe, la herramienta anexa el resultado al final del archivo.

## <a name="remarks"></a>Comentarios

- Este modificador realiza la misma acción que el comando de menú **Recompilar solución** en el IDE.

- Escriba las cadenas que incluyen espacios entre comillas dobles.

- Se puede mostrar información de resumen de las limpiezas y compilaciones, incluidos los errores, en la **ventana de comandos** o en cualquier archivo de registro especificado con el modificador [/Out](out-devenv-exe.md).

## <a name="example"></a>Ejemplo

En este ejemplo se limpia y recompila el proyecto `CSharpWinApp` con la configuración de compilación del proyecto `Debug` en `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)