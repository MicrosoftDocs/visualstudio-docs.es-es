---
title: -DoNotLoadProjects (devenv.exe)
description: Obtenga información sobre cómo usar el modificador de la línea de comandos DoNotLoadProjects para abrir la solución especificada sin cargar ningún proyecto.
ms.custom: SEO-VS-2020
ms.date: 04/30/2019
ms.topic: reference
helpviewer_keywords:
- Devenv, /DoNotLoadProjects switch
- /DoNotLoadProjects Devenv switch
- DoNotLoadProjects Devenv switch
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fb43d3a12e50d3f4a7af43721a5e93b769da28ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907590"
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

Necesario. Ruta de acceso completa y nombre de la solución que se va a abrir.

## <a name="example"></a>Ejemplo

En el ejemplo se abre la solución MySln.sln sin cargar ningún proyecto.

```shell
devenv /donotloadprojects MySln.sln
```

## <a name="see-also"></a>Consulte también

- [Soluciones filtradas en Visual Studio](../filtered-solutions.md)
- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
