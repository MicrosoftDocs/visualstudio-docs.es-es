---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ebeba5afc1eb50703f62e386f7453d7c0c3c1f6
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227192"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Compila y ejecuta el proyecto o solución especificados y, después, cierra el entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumentos

- *SolutionName*

  Ruta de acceso completa y nombre de un archivo de solución.

- *ProjectName*

  Ruta de acceso completa y nombre de un archivo de proyecto.

- `/Out` *OutputFilename*

  Opcional. Nombre de un archivo que quiera enviar al resultado de la herramienta. Si el archivo ya existe, la herramienta anexa el resultado al final del archivo.

## <a name="remarks"></a>Comentarios

Compila y ejecuta el proyecto o solución especificados según los ajustes indicados para la configuración de soluciones activas. Este modificador minimiza el IDE mientras se ejecuta el proyecto o la solución. Asimismo, cierra el IDE al terminar de ejecutarse el proyecto o la solución.

- Escriba las cadenas que incluyen espacios entre comillas dobles.

- Se puede mostrar información de resumen, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/Out`.

## <a name="example"></a>Ejemplo

En este ejemplo se ejecuta la solución `MySolution` en un IDE minimizado con la configuración de implementación activa y, después, se cierra el IDE.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)