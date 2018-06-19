---
title: -Runexit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e2ce262b219b46d543389ac6a8ae8d71466419f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31944445"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
Compila y ejecuta el proyecto o solución especificados y, después, cierra el entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumentos
 `SolutionName`

 Obligatorio. Ruta de acceso completa y nombre de un archivo de solución.

 `ProjectName`

 Obligatorio. Ruta de acceso completa y nombre de un archivo de proyecto.

## <a name="remarks"></a>Comentarios
 Compila y ejecuta el proyecto o solución especificados según los ajustes indicados para la configuración de soluciones activas. Este modificador minimiza el IDE mientras se ejecutan el proyecto o la solución, y cierra el IDE una vez que el proyecto o la solución hayan acabado de ejecutarse.

-   Escriba las cadenas que incluyen espacios entre comillas dobles.

-   Se puede mostrar información de resumen, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.

## <a name="example"></a>Ejemplo
 En este ejemplo se ejecuta la solución `MySolution` en un IDE minimizado con la configuración de implementación activa y, después, se cierra el IDE.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)