---
title: -Run (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d8e89a223ef43d7d2235772940a05b7fb42c0f8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996342"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Compila y ejecuta el proyecto o la solución especificados.

## <a name="syntax"></a>Sintaxis

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Ruta de acceso completa y nombre de un archivo de solución.

- *ProjectName*

  Ruta de acceso completa y nombre de un archivo de proyecto.

- `/Out` *OutputFilename*

  Opcional. Nombre de un archivo que quiera enviar al resultado de la herramienta. Si el archivo ya existe, la herramienta anexa el resultado al final del archivo.

## <a name="remarks"></a>Comentarios

Compila y ejecuta el proyecto o solución especificados según los ajustes indicados para la configuración de soluciones activas. Este modificador inicia el IDE y lo deja activo después de finalizarse la ejecución del proyecto o solución.

- Escriba las cadenas que incluyen espacios entre comillas dobles.

- Se puede mostrar información de resumen, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/Out`.

## <a name="example"></a>Ejemplo

En este ejemplo se ejecuta la solución `MySolution` con la configuración de implementación activa.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)