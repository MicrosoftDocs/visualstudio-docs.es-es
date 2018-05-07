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
ms.openlocfilehash: 0f3d78ebb63434df38735bdf24e9d4fcba8f172c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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