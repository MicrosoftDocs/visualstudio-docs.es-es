---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a414fde4dee401016e997fa5d6890da2ae8d9d53
ms.sourcegitcommit: db30651dc0ce4d0b274479b23a6bd102a5559098
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2019
ms.locfileid: "65083933"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

**Novedades de Visual Studio 2019 versión 16.1**

Abre la solución especificada sin cargar ningún proyecto. Para más información, vea [Soluciones filtradas en Visual Studio](../filtered-solutions.md).

## <a name="syntax"></a>Sintaxis

```shell
devenv /DoNotLoadProjects SolutionName
```

## <a name="arguments"></a>Argumentos

*SolutionName*

Obligatorio. Ruta de acceso completa y nombre de la solución que se va a abrir.

## <a name="example"></a>Ejemplo

En el ejemplo se abre la solución MySln.sln sin cargar ningún proyecto.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Vea también

- [Soluciones filtradas en Visual Studio](../filtered-solutions.md)
- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
