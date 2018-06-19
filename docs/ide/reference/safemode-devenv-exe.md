---
title: -SafeMode (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: c2c678d7304c879cf42c24de9d83704971043676
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704153"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
Inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro, cargando solo el entorno y los servicios predeterminados.

## <a name="syntax"></a>Sintaxis

```cmd
devenv /SafeMode
```

## <a name="remarks"></a>Comentarios
 Este modificador evita que se carguen todos los VSPackages de terceros cuando se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], lo que garantiza una ejecución estable.

## <a name="description"></a>Description
 En el ejemplo siguiente, se inicia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en modo seguro.

## <a name="code"></a>Código

```cmd
Devenv.exe /SafeMode
```

## <a name="see-also"></a>Vea también

- [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)