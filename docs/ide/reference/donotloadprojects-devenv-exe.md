---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51e3341082ff354fc8bc87a89b3d7bc56e4e7887
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569860"
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
