---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f180a45b274ec3042b7e150a43b5e8681fafcfed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593595"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Inicia Visual Studio en modo seguro y carga solo el entorno y los servicios predeterminados.

## <a name="syntax"></a>Sintaxis

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Observaciones

Este modificador impide que todos los paquetes de Visual Studio de terceros se carguen cuando se inicie Visual Studio, lo que permite una ejecución estable.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se inicia Visual Studio en modo seguro.

```shell
devenv /safemode
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)
