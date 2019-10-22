---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14b2ac3a80a9e17e0c554f56ae8e31ac32450c5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62945484"
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