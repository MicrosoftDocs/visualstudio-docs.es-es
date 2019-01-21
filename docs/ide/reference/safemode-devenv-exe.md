---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 092cc1fc3267113e862646b7572e9091b8f6ddef
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227205"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Inicia Visual Studio en modo seguro y carga solo el entorno y los servicios predeterminados.

## <a name="syntax"></a>Sintaxis

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Comentarios

Este modificador impide que todos los paquetes de Visual Studio de terceros se carguen cuando se inicie Visual Studio, lo que permite una ejecución estable.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se inicia Visual Studio en modo seguro.

```shell
devenv /safemode
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)