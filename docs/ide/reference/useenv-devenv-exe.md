---
title: -UseEnv (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5fd76e44b2e503bd7b444e83bb9a64abceeaa561
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Inicia Visual Studio y carga las variables de entorno en el cuadro de diálogo **Directorios de VC++**.

> [!NOTE]
> Este modificador se instala con la carga de trabajo **Desarrollo para el escritorio con C++**.

## <a name="syntax"></a>Sintaxis

```shell
Devenv /useenv
```

## <a name="example"></a>Ejemplo

En este ejemplo, se inicia Visual Studio y se cargan las variables de entorno en el cuadro de diálogo **Directorios de VC++**.

```shell
Devenv.exe /useenv
```

## <a name="see-also"></a>Vea también

* [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)