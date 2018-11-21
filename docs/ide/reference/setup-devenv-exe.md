---
title: Conmutador /setup devenv.exe
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: eca577c0e4646821262c953cf48256937eed386c
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948381"
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

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)