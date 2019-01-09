---
title: -ResetSkipPkgs (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: a892902e129044549f781648d34bf058bf6eae9b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853637"
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