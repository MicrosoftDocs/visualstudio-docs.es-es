---
title: -Out (devenv.exe)
description: Obtenga información sobre cómo usar el modificador Out de la línea de comandos de devenv para especificar un archivo en el que almacenar y mostrar errores al ejecutar, ejecutar y salir, actualizar, compilar, recompilar, limpiar o implementar una solución.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db5a67031d48c55a4bd9c668335360897bcca62b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932194"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Especifica un archivo para almacenar y mostrar errores al [ejecutar](run-devenv-exe.md), [ejecutar y salir](runexit-devenv-exe.md), [actualizar](upgrade-devenv-exe.md), [compilar](build-devenv-exe.md), [recompilar](rebuild-devenv-exe.md), [limpiar](clean-devenv-exe.md) o [implementar](deploy-devenv-exe.md) una solución.

## <a name="syntax"></a>Sintaxis

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumentos

- *FileName*

  Necesario. Ruta de acceso y nombre del archivo que recibirá los errores al compilar un ejecutable.

## <a name="remarks"></a>Comentarios

Si se especifica un nombre de archivo inexistente, el archivo se creará automáticamente. Si el archivo ya existe, los resultados se anexan al contenido existente del archivo.

Los errores de compilación de la línea de comandos se muestran en la **ventana de comandos** y en la vista Generador de soluciones de la ventana **Salida**. Este modificador es útil para ver los resultados de las compilaciones desatendidas.

## <a name="example"></a>Ejemplo

En este ejemplo se ejecuta `MySolution` y se escriben los errores en el archivo `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
