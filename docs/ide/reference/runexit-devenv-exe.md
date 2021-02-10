---
title: -RunExit (devenv.exe)
description: Obtenga información sobre cómo usar el modificador RunExit de la línea de comandos de devenv para compilar y ejecutar el proyecto o la solución especificados y, después, cerrar el IDE.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 695996a6bde054d4e9ae79efdef1955ef93ef527
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957886"
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
