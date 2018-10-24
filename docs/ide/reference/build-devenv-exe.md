---
title: Modificador Build de DevEnv
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdd510e523aaabc468c1f01626593e51d0ad1558
ms.sourcegitcommit: 9571742f4a808c75b1034aa72fc24b54bc50692e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410967"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Compila una solución mediante un archivo de configuración de solución especificado.

## <a name="syntax"></a>Sintaxis

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argumentos

|||
|-|-|
|*SolutionName*|Obligatorio. Ruta de acceso completa y nombre del archivo de solución.|
|*SolnConfigName*|Obligatorio. El nombre de la configuración de solución que se usará para compilar la solución mencionada en *SolutionName*. Si hay varias plataformas de solución disponibles, también se debe especificar la plataforma, por ejemplo **"Debug\|Win32"**.|
|/project *ProjName*|Opcional. Ruta de acceso y nombre de un archivo de proyecto dentro de la solución. Puede escribir una ruta de acceso relativa desde la carpeta *SolutionName* al archivo del proyecto (o el nombre para mostrar del proyecto), o bien la ruta de acceso completa y el nombre del archivo del proyecto.|
|/projectconfig *ProjConfigName*|Opcional. El nombre de una configuración de compilación de proyecto que se va a usar para crear el proyecto mencionado. Si hay varias plataformas de proyecto disponibles, también se debe especificar la plataforma, por ejemplo **"Debug\|Win32"**.|

## <a name="remarks"></a>Comentarios

- El modificador **/build** realiza la misma función que el comando de menú **Compilar solución** en el entorno de desarrollo integrado (IDE).

- Escriba las cadenas que incluyen espacios entre comillas dobles.

- Se puede mostrar la información de resumen de las compilaciones, incluidos los errores, en la ventana de comandos, o bien en cualquier archivo de registro especificado con el modificador **/out**.

- El modificador **/build** solo compila proyectos que han cambiado desde la última compilación. Para compilar todos los proyectos en una solución, use [/rebuild](../../ide/reference/rebuild-devenv-exe.md) en su lugar.

- Si recibe un mensaje de error que dice **Configuración del proyecto no válida**, asegúrese de que ha especificado una plataforma de solución o de proyecto, por ejemplo **"Debug\|Win32"**.

## <a name="example"></a>Ejemplo

El comando siguiente compila el proyecto "CSharpConsoleApp", con la configuración de compilación de proyecto "Debug" dentro de la configuración de solución "Debug" de "MySolution".

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Vea también

- [Compilación y limpieza de proyectos y soluciones](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)