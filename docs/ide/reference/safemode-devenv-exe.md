---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
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
ms.openlocfilehash: ed14c3ec0da75df37c5a006f4e25240ac6630d20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949659"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro, cargando solo el entorno y los servicios predeterminados.

## <a name="syntax"></a>Sintaxis

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Comentarios
 Este modificador evita que se carguen todos los VSPackages de terceros cuando se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], lo que garantiza una ejecución estable.

## <a name="description"></a>Descripción
 En el ejemplo siguiente, se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro.

## <a name="code"></a>Código

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)