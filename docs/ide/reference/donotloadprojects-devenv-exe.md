---
title: -DoNotLoadProjects (devenv.exe)
ms.date: 03/11/2019
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
ms.openlocfilehash: de757e7022339b11f6d7c04ea7315abf685da24c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428052"
---
# <a name="donotloadprojects-devenvexe"></a>/DoNotLoadProjects (devenv.exe)

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
