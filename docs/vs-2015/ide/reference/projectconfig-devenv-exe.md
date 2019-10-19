---
title: -ProjectConfig (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a33c7cbaef473e75631bb4ac6c0d217198cbf250
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662087"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica una configuración de compilación de proyecto que se aplicará al compilar, limpiar, recompilar o implementar el proyecto especificado en el argumento `/project`.

## <a name="syntax"></a>Sintaxis

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumentos
 /Build compila el proyecto especificado por `/project` `ProjName`.

 /Clean limpia todos los archivos intermedios y directorios de salida creados durante una compilación.

 /Rebuild limpia y crea el proyecto especificado por `/project` `ProjName`.

 /deploy especifica que el proyecto se implementará después de una compilación o recompilación.

 `SolnConfigName` Obligatorio. El nombre de la configuración de solución que se aplicará a la solución mencionada en `SolutionName`.

 `SolutionName` Obligatorio. Ruta de acceso completa y nombre del archivo de solución.

 /project `ProjName` Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede especificar una ruta de acceso relativa desde la carpeta `SolutionName` al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.

 /projectconfig `ProjConfigName` Opcional. El nombre de una configuración de compilación de proyecto que se aplicará al `/project` mencionado.

## <a name="remarks"></a>Comentarios

- Se debe usar con el modificador `/project` como parte de un comando `devenv /build`, /`clean`, `/rebuild` o `/deploy`.

- Escriba las cadenas que incluyen espacios entre comillas dobles.

- Se puede mostrar información de resumen de las compilaciones, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.

## <a name="example"></a>Ejemplo
 Este ejemplo compila el proyecto `CSharpConsoleApp`, mediante la configuración de compilación de proyecto `Debug` en la configuración de solución `Debug` de `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Otras referencias
 [Modificadores de la línea de comandos de devenv](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
