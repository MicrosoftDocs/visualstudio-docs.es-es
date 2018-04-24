---
title: Conmutador /setup devenv.exe | Microsoft Docs
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: eee6e30a7489f5097cb17a19513c2a423187c827
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)

El conmutador /Setup provoca que Visual Studio combine los metadatos de recursos que describen menús, barras de herramientas y grupos de comandos de todos los VSPackages disponibles.

## <a name="syntax"></a>Sintaxis

```shell
devenv /setup
```

## <a name="remarks"></a>Comentarios

Este modificador no toma ningún argumento. El comando `devenv /setup` suele ser el último paso del proceso de instalación. El uso del conmutador `/setup` no inicia Visual Studio.

> [!NOTE]
> Debe ejecutar `devenv` como administrador para poder usar el modificador `/setup`.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra el último paso de la instalación de una versión de Visual Studio que incluye VSPackages.

```shell
devenv /setup
```

## <a name="see-also"></a>Vea también

[Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)