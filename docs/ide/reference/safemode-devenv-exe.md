---
title: -SafeMode (devenv.exe)
description: Obtenga información sobre cómo usar el modificador SafeMode de la línea de comandos de devenv para iniciar Visual Studio en modo seguro y cargar solo el entorno y los servicios predeterminados.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957873"
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
