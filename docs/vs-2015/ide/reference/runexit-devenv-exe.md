---
title: -Runexit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6d1158a12de8b8adfe20fa6d045b756abf8d7b3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665494"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Compila y ejecuta el proyecto o solución especificados y, después, cierra el entorno de desarrollo integrado (IDE).

## <a name="syntax"></a>Sintaxis

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumentos
 `SolutionName` Obligatorio. Ruta de acceso completa y nombre de un archivo de solución.

 `ProjectName` Obligatorio. Ruta de acceso completa y nombre de un archivo de proyecto.

## <a name="remarks"></a>Observaciones
 Compila y ejecuta el proyecto o solución especificados según los ajustes indicados para la configuración de soluciones activas. Este modificador minimiza el IDE mientras se ejecutan el proyecto o la solución, y cierra el IDE una vez que el proyecto o la solución hayan acabado de ejecutarse.

- Escriba las cadenas que incluyen espacios entre comillas dobles.

- Se puede mostrar información de resumen, incluidos los errores, en la ventana **Comandos** o en cualquier archivo de registro especificado con el modificador `/out`.

## <a name="example"></a>Ejemplo
 En este ejemplo se ejecuta la solución `MySolution` en un IDE minimizado con la configuración de implementación activa y, después, se cierra el IDE.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Consulte también
 [Modificadores de línea de comandos de devenv](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
