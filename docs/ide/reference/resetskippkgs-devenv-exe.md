---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /ResetSkipPkgs Devenv switch
- Devenv, /ResetSkipPkgs switch
- ResetSkipPkgs switch
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbf7a601213c3c02cc35f2d9453eee6b1d39c43e
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="resetskippkgs-devenvexe"></a>/ResetSkipPkgs (devenv.exe)
Borra todas las opciones para omitir la carga agregada a VSPackages por usuarios que quieren evitar problemas al cargar VSPackages. Después, inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintaxis

```cmd
Devenv /ResetSkipPkgs
```

## <a name="remarks"></a>Comentarios
 La presencia de una etiqueta SkipLoading deshabilita la carga de un VSPackage; al borrar la etiqueta, se rehabilita la carga de VSPackage.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente, se borran todas las etiquetas SkipLoading.

```cmd
Devenv.exe /ResetSkipPkgs
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)