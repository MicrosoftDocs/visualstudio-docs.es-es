---
title: -Rebuild (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e462e64df90a7672efa890897b48726a0e764e6c
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
Limpia y, después, compila la configuración de solución especificada.

## <a name="syntax"></a>Sintaxis

```cmd
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumentos
 `SolnConfigName`

 Obligatorio. Nombre de la configuración de solución que se usará para recompilar la solución mencionada en `SolutionName`.

 `SolutionName`

 Obligatorio. Ruta de acceso completa y nombre del archivo de solución.

 /project `ProjName`

 Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede especificar una ruta de acceso relativa desde la carpeta `SolutionName` al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.

 /projectconfig `ProjConfigName`

 Opcional. Nombre de una configuración de compilación de proyecto que se usará para crear el `/project` mencionado.

## <a name="remarks"></a>Comentarios

-   Este modificador realiza la misma función que el comando de menú **Recompilar solución** en el entorno de desarrollo integrado (IDE).

-   Escriba las cadenas que incluyen espacios entre comillas dobles.

-   Se puede mostrar información de resumen de las limpiezas y compilaciones, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.

## <a name="example"></a>Ejemplo
 En este ejemplo se limpia y se recompila el proyecto `CSharpWinApp` mediante la configuración de compilación de proyecto `Debug` en la configuración de solución `Debug` de `MySolution`.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)