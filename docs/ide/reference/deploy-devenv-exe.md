---
title: -Deploy (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0297058fea98568551f54d8960e62f80bb35ccd7
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948886"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
Implementa una solución después de una compilación o recompilación. Solo se aplica a los proyectos de código administrado.

## <a name="syntax"></a>Sintaxis

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Argumentos
 `SolnConfigName`

 Obligatorio. El nombre de la configuración de solución que se usará para compilar la solución mencionada en `SolutionName`.

 `SolutionName`

 Obligatorio. Ruta de acceso completa y nombre del archivo de solución.

 /project `ProjName`

 Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede especificar una ruta de acceso relativa desde la carpeta `SolutionName` al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.

 /projectconfig `ProjConfigName`

 Opcional. El nombre de una configuración de compilación de proyecto que se usará para crear el `/project` mencionado.

## <a name="remarks"></a>Comentarios
 El proyecto especificado debe ser un proyecto de implementación. Si el proyecto especificado no es un proyecto de implementación, se producirá un error cuando se pase el proyecto que se ha compilado para implementarse.

 Escriba las cadenas que incluyen espacios entre comillas dobles.

 Se puede mostrar información de resumen de las compilaciones, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.

## <a name="example"></a>Ejemplo
 Este ejemplo implementa el proyecto `CSharpConsoleApp`, mediante la configuración de compilación de proyecto `Release` en la configuración de solución `Release` de `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)