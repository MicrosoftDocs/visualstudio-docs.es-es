---
title: Modificador ProjectConfig de DevEnv
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44f5d4479658b450074ba35f2759a273bb584e0a
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764659"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Especifica una configuración de compilación de proyecto que se aplicará al compilar, limpiar, recompilar o implementar el proyecto especificado en el argumento **/project**.

## <a name="syntax"></a>Sintaxis

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumentos

|||
|-|-|
|/build|Compila el proyecto especificado por el argumento **/project**.|
|/clean|Limpia todos los archivos intermedios y directorios de salida creados durante una compilación.|
|/rebuild|Limpia y después compila el proyecto especificado por el argumento **/project**.|
|/deploy|Especifica que el proyecto se implementará después de una compilación o recompilación.|
|*SolnConfigName*|Obligatorio. El nombre de la configuración de solución que se aplicará a la solución indicada en *SolutionName*. Si hay varias plataformas de solución disponibles, también se debe especificar la plataforma, por ejemplo **"Debug\|Win32"**.|
|*SolutionName*|Obligatorio. Ruta de acceso completa y nombre del archivo de solución.|
|/project *ProjName*|Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede escribir una ruta de acceso relativa desde la carpeta *SolutionName* al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.|
|/projectconfig *ProjConfigName*|Opcional. El nombre de una configuración de compilación de proyecto que se aplicará al proyecto especificado por el argumento **/project**. Si hay varias plataformas de solución disponibles, también se debe especificar la plataforma, por ejemplo **"Debug\|Win32"**.|

## <a name="remarks"></a>Comentarios

Se debe usar el modificador **/projectconfig** con el modificador **/project** como parte de un comando **/build**, **/clean**, **/rebuild** o **/deploy**.

Escriba las cadenas que incluyen espacios entre comillas dobles.

Se puede mostrar la información de resumen de las compilaciones, incluidos los errores, en la ventana de comandos, o bien en cualquier archivo de registro especificado con el modificador **/out**.

## <a name="example"></a>Ejemplo

El comando siguiente compila el proyecto "CSharpConsoleApp", con la configuración de compilación de proyecto "Debug" dentro de la configuración de solución "Debug" de "MySolution":

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)